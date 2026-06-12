---
title: "How solid is PHP with MS SQL Server?"
date: 2010-07-12
forum: Programming Talk
---

### Post by Lucky. on 2010-07-12
The company I work at is a Microsoft house.  However I personally gravitate towards with PHP/MySQL and have some experience with it at home.  I know you can run PHP on IIS, but I'd rather go Apache & Ubuntu.

We're about to begin development on a corporate website with a shopping cart, etc.  This would be a great chance for us to jump from our old ASP site to a PHP site.  However if we're going to use a shopping cart that must integrate with our Microsoft SQL Server (MySQL is not permitted), then the only thing that worries me is how stable has the history between the two been?

Seems like a lot of Open Source technologies brush elbows with Microsoft technologies, but then they break at some point (usually MS's fault).  Does Apache-PHP work with with MS SQL?  If so, how long has it existed and worked well?  Would anybody recommend it for an enterprise-grade website, or is its future too sketchy?

---

### Post by brian_swan on 2010-07-16
[Disclaimer: I work for Microsoft and focus on providing technical content for PHP developers who wan to use MS technologies.)
 
Microsoft has done lots of work in the last couple of years to improve performance and stability of PHP on Windows (especially with IIS and the FastCGI module). Microsoft has also released the [SQL Server Driver for PHP]("http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=df4d9cc9-459c-4d75-a503-ae3fceb85860") (which is better than the php_mssql.dll driver if you are running on Windows). Installation/configuration of PHP/IIS/SQL Sever Express/etc are much easier than in the past with the [Web Platform Installer]("http://www.microsoft.com/web/downloads/platform.aspx"). Here are some other resources that might be interesting/helpful:
[LIST]
[*][http://php.iis.net/](http://php.iis.net/)
[*][http://blogs.msdn.com/b/sqlphp/](http://blogs.msdn.com/b/sqlphp/)
[*][http://blogs.msdn.com/b/brian_swan/](http://blogs.msdn.com/b/brian_swan/)
[/LIST]Hope that helps.
 
-Brian

---

