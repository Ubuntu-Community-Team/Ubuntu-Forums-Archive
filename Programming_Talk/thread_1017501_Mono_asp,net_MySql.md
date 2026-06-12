---
title: "Mono asp,net MySql"
date: 2008-12-21
forum: Programming Talk
---

### Post by grognut on 2008-12-21
Hi All,

I'm running a fresh install of LTS 6.06 as a parallel system to my web server with mono..., apache, mod-mono, mysql, php etc. I followed the tutorials for the installation and all sees to run OK.
I've tried the asp example and they are served OK. So there doesn't appear to anything wrong with the basic installation. PhpMySql also runs and MySql is running.

So everything appears OK until I try to do something different. As a novice at C# I kinda expect this to happen.[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

I'm trying to use MySql.Data to display data on a web page but I'm having problems.

I used an example from the web but I get the error
```

error CS0246: The type or namespace name `Data.MySqlClient' could not be found. Are you missing a using directive or an assembly reference?
```

whenever I run the page.

I added 

```
    <compilation>
      <assemblies>
        <add assembly="MySql.Data, Version=5.2.3.0, Culture=neutral, PublicKeyToken=c5687fc88969c44d"/>
      </assemblies>
    </compilation>
```
in the system.web section of the web.config file in the root page but with no success.

So I created a simple app using MonoDevelop (which had using gtk etc in it) and added the line
```
using MySql.Data.MySqlClient;
```
When I compile I get 

```
The type or namespace name `MySql' could not be found. Are you missing a using directive or an assembly reference?(CS0246)
```

To check that I have MySql.Data I use gacutil -l MySql.Data
And get
&#65279;```
The following assemblies are installed into the GAC:
MySql.Data, Version=5.2.3.0, Culture=neutral, PublicKeyToken=c5687fc88969c44d
Number of items = 1
```


In summary my problem is that gacutil thinks it's installed but it can be found at run time. Can anyone help me with this?

I'm knew to Mono and C# so I assume I guess there's some config file that needs to be set up.

Thanking you in advance

grognut

---

### Post by directhex on 2008-12-21
Your standalone app needs to use a reference - in Monodevelop, right click on the 'references' in the project pane, edit references, and ensure then box is ticked for mysql

As for the ASP.NET, try <%@ Import Namespace="MySql.Data.MySqlClient" %>

See [http://townx.org/blog/elliot/using-mysql-asp-net-under-mono-linux](http://townx.org/blog/elliot/using-mysql-asp-net-under-mono-linux) for simple examples

---

### Post by grognut on 2008-12-21
Hi directhex,

Thank you for response.

Mysql is not listed in the references. This is probably why I have a problem.

Could I trouble you further and ask how I get it into the reference list. gacutil thinks it's installed so is there another process i have to do for MonoDevelop to see it.

For the asp part I already have 
<%@ Import Namespace="MySql.Data.MySqlClient" %> at the top of the file and this is the line that is complained about.
In fact the example I'm using is from [http://townx.org/blog/elliot/using-mysql-asp-net-under-mono-linux](http://townx.org/blog/elliot/using-mysql-asp-net-under-mono-linux) but unfortunately I can't get it to work.
I guess that although gacutil thinks MySql is installed there must be something missing from my set up.

If you have any other suggestions I will welcome them.

Thanking you again

grognut

---

### Post by mssever on 2008-12-21
I can't help you with Mono, but I was wondering why you're using a fresh install of Dapper (6.06). It's quite outdated by now, and the Mono situation is probably changed somewhat. If you want to run an LTS version, install Hardy (8.04).

I can see perhaps not wanting to upgrade a particular machine, but I don't understand using an obsolete version in a fresh install.

---

### Post by directhex on 2008-12-21
> **mssever said:**
> I can't help you with Mono, but I was wondering why you're using a fresh install of Dapper (6.06). It's quite outdated by now, and the Mono situation is probably changed somewhat. If you want to run an LTS version, install Hardy (8.04).

I can see perhaps not wanting to upgrade a particular machine, but I don't understand using an obsolete version in a fresh install.

Well spotted.

libmysql5.0-cil requires Hardy or above (where Hardy has 5.0.8)

---

### Post by grognut on 2008-12-21
Hi mssever,

I have a server with 6.06lts running now for a 1.5 years or so (268 days since the last boot). Basically I want this server for asp pages so I'm doing a parallel install so if anything breaks I know what not to do.

I may try upgrading the parallel install once everything works and if this is OK then upgrade the server providing there are good technical reasons. I am a bit of a "if it works, don't fix it" type of guy so if there aren't good technical reasons I probably won't.

Thanking you for your comments

grognut

---

### Post by grognut on 2008-12-21
Hi directhex,

Thank you for responding.

Are you saying that the only MySql CLI connector is libmysql5.0-cil and that requires 8.04lts?
If so I will need to upgrade. I'm glad I used a parallel system.:)

Would that explain why MySql.Data is invisible or would this cause run time errors?



Thank you.

grognut

---

### Post by mssever on 2008-12-21
> **grognut said:**
> I have a server with 6.06lts running now for a 1.5 years or so (268 days since the last boot). Basically I want this server for asp pages so I'm doing a parallel install so if anything breaks I know what not to do.

I may try upgrading the parallel install once everything works and if this is OK then upgrade the server providing there are good technical reasons. I am a bit of a "if it works, don't fix it" type of guy so if there aren't good technical reasons I probably won't.
One thing to consider is that if you go too long before upgrading, you might have a lot more trouble when you do decide to upgrade--or maybe even when you decide to install new software.

I experienced this a number of years ago while running RedHat 7.3. For several reasons, I decided against upgrading. Fast forward several years, and I needed to install PHP 5. The PHP 5 RPMs I found wouldn't install because some system library (libc perhaps--I don't remember anymore) was too old and incompatible. So, I decided to build from source. But some things on my system were too old that I ended up upgrading--from source--Apache, GCC, libc, and a whole bunch of other stuff. It took me several days and was a royal pain. Plus, I never managed to get everything working quite right. That's when I decided to switch to a more modern distro and wound up with Ubuntu Dapper. Granted, APT (which Ubuntu uses) is more advanced than pre-yum RPM, and would probably recover a bit easier. But you should at least be aware of the risk.

---

### Post by grognut on 2008-12-21
Hi msserver,

Good points.

Basically don't leave it to long if you want newer technologies.

It seems from your comments and directhex's I will need to upgrade. So I'll try on the parallel system first.

Thanks

grognut

---

### Post by grognut on 2008-12-30
Hi Guys

I tried to upgrade but it was not successful. After doing an update I tried to upgrade the version that had mono/apache working on and it reported many problems, one of which was the failure to install aptitude. So i did a re-install and this time I only installed apache with php5 and mysql. These all worked so I tried another upgrade and this failed. No fonts again.

I would have thought that this should have been seamless.

Any thoughts.

Regards
Grognut

---

### Post by mssever on 2008-12-30
> **grognut said:**
> Hi Guys

I tried to upgrade but it was not successful. After doing an update I tried to upgrade the version that had mono/apache working on and it reported many problems, one of which was the failure to install aptitude. So i did a re-install and this time I only installed apache with php5 and mysql. These all worked so I tried another upgrade and this failed. No fonts again.

I would have thought that this should have been seamless.

Any thoughts.

Regards
Grognut
It's impossible to say much without specific details. What errors were there? What did you do leading up to the errors? What was your system setup prior to the upgrade? Additionally, I don't understand why you did an upgrade after a re-install. Why not just install the proper version in the first place? And what do fonts have to do with anything?

---

### Post by grognut on 2008-12-30
msserver, thanks for your response.

I wasn't looking for a definitive answer jusy a few thoughts of possible causes or whether anyone else had had similar problems.

I realise that without a full trace no-one could give a specific answer. If possible I could post a log (if I knew where to find it) but I want to try again first and then start a new thread in Installation & Upgrades.

The reason that I'm trying an upgrade is that I want to eventually upgrade a server. About a year ago I spent over a week of evenings setting up the server and if I do a re-install I'll have to go throught it all again. (Good learning but I don't have the time). If I upgrade there should only be a small amount of work. Then I can get mono, asp.net ... working on the upgraded server.

> And what do fonts have to do with anything? This was just one indication of the problems. After the install the system reboots I get a login screen with square blocks where the characters should be. I don't mind the occasional computer game but navigating an operating system with "Guess the message" is beyond me:)

I should add that I'm tying all this on a parallel system.

Seasonal greetings

Grognut

---

### Post by grognut on 2009-01-23
Hi Guys,

I now have my server running 8.04 with Mono/mod-mono etc and help from directhex BUT I still can't access mysql.

I've downloaded mysql connector and did 
```
gacutil -i MySql.Data.dll
```
and ```
gacutil -l MySql.Data.dll
``` shows is as present.

When I try to use the example from [HTML]http://townx.org/blog/elliot/using-m...der-mono-linux[/HTML] I get 
```
Parser Error Message: Assembly MySql.Data.dll not found
```

Do I need to install libmysql5.0-cil as well or is ther more to this?

Cheers

grognut.

---

### Post by mssever on 2009-01-23
> **grognut said:**
> Do I need to install libmysql5.0-cil as wellProbably. Try it. I'm not a Mono user, so I don't really know how it works, but from reading the package description, it appears that that's what you're looking for.

---

### Post by directhex on 2009-01-23
Did you set up your web.config as directed in your link? This file lists all the GAC assemblies which should be made available to your app

---

### Post by grognut on 2009-01-23
Hi Directhex,
 my web.config is

```
<configuration>
  <system.web>
    <compilation debug="true">
      <assemblies>
        <add assembly="MySql.Data.dll"/> 
      </assemblies>
    </compilation>
	<customErrors mode="Off"/>
  </system.web>
</configuration>

```

As you can see it's in there but it it can't be found.

Hi mssever,

Have insalled Debian Etch and Mono/mono_mono.. on another machine and this does not have this library install but the application I'm trying works. Hence the confusion.

I will try installing it later. I guess it won't damage anything.


Thanks 

Grognut

---

### Post by grognut on 2009-01-23
Hi,

Installed libmysql5.0-cil but with no change.

Do you have any ideas on how to debug?


Thnaks

grognut

---

