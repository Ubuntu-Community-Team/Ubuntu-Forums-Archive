---
title: "Problem passing Bash variable to MySQL"
date: 2007-08-04
forum: Programming Talk
---

### Post by UltraMathMan on 2007-08-04
Hello - I'm trying to use a variable in a bash script as part of a MySQL query later in the same script. I think I have the syntax right, but for some reason I'm not getting the information in MySQL table. By the way, this script is for a mac, hence the slightly different ifconfig statement.

```
macaddress=`ifconfig en0 |grep ether`
macaddress=${macaddress:6}
fullname=`mysql -u root --password='pass_here' -D rasa07 -e "SELECT fullname FROM data WHERE macaddress = '$macaddress'"` 
fullname=${fullname:9}
echo $fullname
``` I know (and checked several times) that the machine's MAC address **is** in the MySQL table and ```
shortname=testuser
macaddress=`mysql -u root --password='pass_here' -D rasa07 -e "SELECT macaddress FROM data WHERE shortname = '$shortname'"`
echo $shortname
``` works fine. I know bash variables are untyped but it seems as though there is something "wrong" with $macaddress. Any help would be appreciated.

---

### Post by UltraMathMan on 2007-08-04
So I figured it out ```
macaddress=${macaddress:6}
``` should be ```
macaddress=${macaddress:7}
``` The first command left a leading space that was preventing a match. I wrote a script echoing $macaddress and the text version prefixed by "var input:" and "text input:". After that the problem was clear. :lolflag:

Hope this helps someone with a similar problem :)

---

