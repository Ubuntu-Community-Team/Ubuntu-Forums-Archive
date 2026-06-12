---
title: "[SOLVED] Problem with Grails connecting to local MySQL database"
date: 2008-10-10
forum: Programming Talk
---

### Post by stefanadelbert on 2008-10-10
I'm working my way through a Groovy/Grails tutorial that describes the creation of a racetrack application, which can be found here: [http://www.infoq.com/minibooks/grails]("http://www.infoq.com/minibooks/grails").

I've got to the point where I have the application working against the in-memory database. I now want to get it working against an actual MySQL database.

I've created the database from the CLI and can inspect it (i.e. it does actually exist).

I have downloaded the MySQL java connector (ver 5.1.6) and have it in the <grails_projname>/lib directory.

I can run my grails app, but when attempt to access one of the controllers, I get this error:

> [15523] errors.GrailsExceptionResolver could not execute query; nested exception is org.hibernate.exception.SQLGrammarException: could not execute query

The actual problems seems to be:

> Caused by: java.sql.SQLException: Table not found in statement [select top ? this_.id as id1_0_, this_.version as version1_0_, this_.city as city1_0_, this_.cost as cost1_0_, this_.distance as distance1_0_, this_.max_runners as max6_1_0_, this_.name as name1_0_, this_.start_date_time as start8_1_0_, this_.state as state1_0_ from race this_]

This is not surprising because the table "race" doesn't exist in the database. I suppose that this means that the database table has not been created by the grails app.

Here is a section of the DataSource.groovy file:

```

dataSource {
}
hibernate {
}
// environment specific settings
environments {
	development {
		dataSource {
			boolean pooling = true			
			String dbCreate = "update" // one of 'create', 'create-drop','update'
			String url = "jdbc:mysql://localhost/racetrack_dev"
			String driverClassName = "com.mysql.jdbc.Driver"
			String username = "stefan"
			String password = ""
		}
	}
```

Has anyone experienced similar problems? Anyone got any advice?

Many thanks
Stef

---

### Post by stefanadelbert on 2008-10-10
I managed to figure out my own problem before I had even finished writing the original post, but I thought I'd post it anyway and then post a reply too.

I was following a tutorial that was based on an older version of Grails, so the format of the DataSource.groovy file I was using wasn't right or something...

Anyway, my DataSource.groovy now looks like this and it works:

```

dataSource {
}
hibernate {
    cache.use_second_level_cache=true
    cache.use_query_cache=true
    cache.provider_class='com.opensymphony.oscache.hibernate.OSCacheProvider'
}
// environment specific settings
environments {
	development {
		dataSource {
			pooled = true			
			dbCreate = "update" // one of 'create', 'create-drop','update'
			url = "jdbc:mysql://localhost/racetrack_dev"
			driverClassName = "com.mysql.jdbc.Driver"
			username = "stefan"
			password = ""
		}
	}
...

```

---

### Post by jkuehn on 2008-10-12
Hi Stefan, thank you very much for your solution! I was struggling with the same problem for an hour now, very annoying. 

Obviously i used the same outdated example configuration as you did. It turned out to be the static typing:

```

url = "jdbc:mysql://localhost/racetrack_dev"
```
is fine, but
```

String url = "jdbc:mysql://localhost/racetrack_dev"
```
is not!

If someone knows the reason for this, i really would like to know.

Greetings,
Juri

---

