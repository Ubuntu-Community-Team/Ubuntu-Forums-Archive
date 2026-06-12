---
title: "Nutch search in Tomcat not showing up"
date: 2008-06-04
forum: Programming Talk
---

### Post by ultraloveninja on 2008-06-04
So, I've installed nutch in 8.04 and I am using this guide to run it:


[http://wiki.apache.org/nutch/GettingNutchRunningWithDebian](http://wiki.apache.org/nutch/GettingNutchRunningWithDebian)

cause it was easier to follow than the install for ubuntu.
anyways, when I get to this step to set up the search:

> And repeat for site2.
Create site1.xml and site2.xml under /usr/share/tomcat5.5-webapps by modifying the distribution nutch-site.xml

<Context path="/site1" docBase="/usr/share/tomcat5.5-webapps/site1"
   debug="0" privileged="true" allowLinking="true">
</Context>

I am a little confused/stuck.
I have done what it's said to do, but it's not showing up in the tomcat app manager.  So I am led to believe that it's not being able to read the xml file that is created, which looks like this:

```
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>

<!-- Put site-specific property overrides in this file. -->

<configuration>

<Context path="/helppages" docBase="/usr/share/tomcat5.5-webapps/helppages"
   debug="0" privileged="true" allowLinking="true">
</Context>

</configuration>
```

is that even right?  
this is where i am a little lost.  I am guessing that tomcat has to read that file correctly in order for it to show in the manager area.

and ideas???

---

### Post by ultraloveninja on 2008-06-04
well,crap.

I guess all it take is a post on here to get it working.

i change the xml file and got rid of the <configuration></configuration>.


now it works!


thanks!!!

---

