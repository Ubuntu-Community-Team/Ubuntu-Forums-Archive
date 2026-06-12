---
title: "Echo bar in $version = 'bar'"
date: 2009-10-10
forum: Programming Talk
---

### Post by FakeOutdoorsman on 2009-10-10
I'm not a programmer at all, but I'm trying to write a bash script that will download a file, check it's md5sum, compare to the online md5sum and then continue.  I am trying to figure this out myself so I can learn, but I am stuck at echoing a value from a file that contains a version number:
```
$version = 'bar'
```
The *bar* is often in the format of *1.2* or *1.2.5* for example.  How do I echo just the *bar*?  Simple stuff, but over my head so far.

---

### Post by ibuclaw on 2009-10-10
> **FakeOutdoorsman said:**
> I'm not a programmer at all, but I'm trying to write a bash script that will download a file, check it's md5sum, compare to the online md5sum and then continue.  I am trying to figure this out myself so I can learn, but I am stuck at echoing a value from a file that contains a version number:
```
$version = 'bar'
```
The *bar* is often in the format of *1.2* or *1.2.5* for example.  How do I echo just the *bar*?  Simple stuff, but over my head so far.

The version number is kept in a file? or is it hard-coded as a string?

If bar is an actual string, you should be doing it like this:
```
version='bar'
```
and then use $version to reference the value.

Regards
Iain

---

### Post by FakeOutdoorsman on 2009-10-10
Thanks for the reply.  The version number is kept in a php file located in the archive that the script downloads, specifically *wordpress/wp-includes/version.php*.  It's the Wordpress version number and an example can be seen here: [version.php](http://core.svn.wordpress.org/trunk/wp-includes/version.php).  Eventually, my script will download *latest.tar.gz* and then compare it's md5sum to the [md5sum shown online](http://wordpress.org/wordpress-2.8.4.md5) for the corresponding version.  Here is what I have so far:

```
#!/bin/bash
version="duh..."
md5sumlocal= `md5sum latest.tar.gz | cut -c1-32`
md5sumonline=`curl http://wordpress.org/wordpress-"$version".md5`

if [ -e "latest.tar.gz" ]; then
        rm -rf latest.tar.gz
fi

wget http://wordpress.org/latest.tar.gz

if [ "$md5sumlocal" != "$md5sumonline" ]; then
        echo
        echo "md5sum failed!"
        exit
fi
```

I can't figure out how to get the *2.8.5* from *$wp_version = '2.8.5';* so I can apply it to the curl command.

Also, a few more questions.  Should I be using *!=* or *-ne*?  What is the difference between *${foo}* and *"$foo"*?

---

### Post by eightmillion on 2009-10-10
> **FakeOutdoorsman said:**
> 
I can't figure out how to get the *2.8.5* from *$wp_version = '2.8.5';* so I can apply it to the curl command.

How about something like this to get the version:
[PHP]version=$(curl -s http://core.svn.wordpress.org/trunk/wp-includes/version.php | awk -F\' '/^\$wp_version/{print $2}')[/PHP]

> **FakeOutdoorsman said:**
> Also, a few more questions.  Should I be using *!=* or *-ne*? 
!= is for comparing strings so it's what you should be using in this particular instance. -ne is for comparing integers.
> **FakeOutdoorsman said:**
> What is the difference between *${foo}* and *"$foo"*?
${foo} is used when you want to clearly delineate variables. Let's say that foo=123, and you want to echo the value of foo plus the word "bar". You might do something like "echo $foobar". Bash will interpret that as the variable foobar and either return the value of $foobar if it's set or nothing at all if it's not. "echo ${foo}bar" will actually echo 123bar. Note that if you use the braces syntax, you still have to quote a variable to maintain spaces. See this example:
[PHP]
$ foo="bar baz"
$ echo $foobar

$ echo ${foo}bar
bar bazbar
$ if [ ${foo} == "bar baz" ];then echo True; fi
bash: [: too many arguments
$ if [ "${foo}" == "bar baz" ];then echo True; fi
True


#Just to demonstrate different comparison operators:
$ if [ "${foo}" -eq "bar baz" ];then echo True; fi
bash: [: bar baz: integer expression expected
[/PHP]

---

### Post by FakeOutdoorsman on 2009-10-11
> **eightmillion said:**
> How about something like this to get the version:
[PHP]version=$(curl -s http://core.svn.wordpress.org/trunk/wp-includes/version.php | awk -F\' '/^\$wp_version/{print $2}')[/PHP]
This works great.  I thought awk was the tool to use, but I just could not figure it out.  I just modified it slightly to get the version from the local version.php instead:

[php]version=$(awk -F\' '/^\$wp_version/{print $2}' wordpress/wp-includes/version.php)[/php]

> != is for comparing strings so it's what you should be using in this particular instance. -ne is for comparing integers.

${foo} is used when you want to clearly delineate variables. Let's say that foo=123, and you want to echo the value of foo plus the word "bar". You might do something like "echo $foobar". Bash will interpret that as the variable foobar and either return the value of $foobar if it's set or nothing at all if it's not. "echo ${foo}bar" will actually echo 123bar. Note that if you use the braces syntax, you still have to quote a variable to maintain spaces. See this example:
[PHP]
$ foo="bar baz"
$ echo $foobar

$ echo ${foo}bar
bar bazbar
$ if [ ${foo} == "bar baz" ];then echo True; fi
bash: [: too many arguments
$ if [ "${foo}" == "bar baz" ];then echo True; fi
True


#Just to demonstrate different comparison operators:
$ if [ "${foo}" -eq "bar baz" ];then echo True; fi
bash: [: bar baz: integer expression expected
[/PHP]

Thanks for the excellent examples describing how this works.  It's very helpful.

---

