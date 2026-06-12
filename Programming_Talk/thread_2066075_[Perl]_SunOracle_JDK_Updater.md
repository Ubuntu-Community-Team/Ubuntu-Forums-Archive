---
title: "[Perl] Sun/Oracle JDK Updater"
date: 2012-10-03
forum: Programming Talk
---

### Post by neil_1 on 2012-10-03
I'm trying to make a script in perl which can check for updates to sun/oracle's java jdk.
I'm a little stuck here since I can’t download the file if I don’t visit their download page and accept the OTN license.

But I do have a cookie which i can use to grab the file using wget.
```

wget --no-cookies --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2Ftechnetwork%2Fjava%2Fjavase%2Fdownloads%2Fjdk-7u7-linux-x64download-1505220.html;" http://download.oracle.com/otn-pub/java/jdk/7u7-b10/jdk-7u7-linux-x64.rpm

```

Here,
```

7u7-b10
```
is the 
```

$version followed by the $update followed by the $build numbers
```
Now, I was having a thought of having my script loop through all possible values for $version, $update and $build. But this is going to take too much time.
Does anyone have a better thought on how to do this ?

---

