# Apollo Docker
This project provide a `docker-compose.yml` file. This is a template for reference

**Note**
Before you start the application. You should config database first.

- Step1: config `ApolloConfigDB`<br/>
Sql file: [sqlFile](https://github.com/ctripcorp/apollo/blob/master/scripts/sql/apolloconfigdb.sql)

- Step2: config `ApolloPortalDB`<br/>
Sql file: [sqlFile](https://github.com/ctripcorp/apollo/blob/master/scripts/sql/apolloportaldb.sql)

- Step3: update ApolloConfigDB data<br/>
Because of using docker, we should change `eureka.service.url`
```sql
update `ApolloConfigDB`.`ServerConfig` set `Value` = 'http://apollo-configservice:8080/eureka/' where `Key` = 'eureka.service.url'
```

- Step4: update ApolloPortalDB data<br/>
According to the apollo-portal environment meta, we should change `apollo.portal.envs`, the following example is a template
```sql
update `ApolloPortalDB`.`ServerConfig` set `Value` = 'local' where `Key` = 'apollo.portal.envs'
```

