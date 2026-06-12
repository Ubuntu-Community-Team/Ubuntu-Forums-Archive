---
title: "PHP executing a bash script"
date: 2006-12-02
forum: Programming Talk
---

### Post by ninocass on 2006-12-02
Hi all

I have written a bash script that wgets the "connected users" page of my wireless router.  It then parses out the connected macs and and displays if the user is online or not:

```

rm -rf /home/nino/macs
rm -rf /home/nino/test
wget -nv -q --http-user=[USERNAME]-O /home/nino/ad-admin-client.htm --http-password=[PASSWORD] http://192.168.11.1/advance/ad-admin-client.htm 
cat /home/nino/ad-admin-client.htm | grep 00: >> /home/nino/macs
cat /home/nino/macs | cut -c84-100 > /home/nino/cutup
rm /home/nino/ad-admin-client.htm

cat  /home/nino/cutup | grep 00:13:CE:2D:A3:A2

echo "<BR>" >> /home/nino/test

case $? in
0)
echo "NINO-IPW ONLINE <BR>" >> /home/nino/test
;;
1)
echo "NINO_IPW OFFLINE<BR>" >> /home/nino/test
;;
esac

cat /home/nino/cutup | grep 00:20:A6:58:97:A7

case $? in
0)
echo "NINO-PROXIM ONLINE<BR>" >> /home/nino/test
;;
1)
echo "NINO_PROXIM OFFLINE<BR>" >> /home/nino/test
;;
esac



cat  /home/nino/cutup | grep 00:0A:95:F1:B1:81

case $? in
0)
echo "DARREN ONLINE<BR>" >> /home/nino/test
;;
1)
echo "DARREN OFFLINE<BR>" >> /home/nino/test
;;
esac

cat /home/nino/cutup | grep 00:0F:B5:09:2D:0B

case $? in
0)
echo "DOM ONLINE<BR>" >> /home/nino/test
;;
1)
echo "DOM OFFLINE<BR>" >> /home/nino/test
;;
esac

cat /home/nino/cutup | grep 00:0F:B5:0A:4F:8B

case $? in
0)
echo "REBECCA ONLINE<BR>" >> /home/nino/test
;;
1)
echo "REBECCA OFFLINE<BR>" >> /home/nino/test
;;
esac

cat /home/nino/cutup | grep 00:0F:B5:42:0C:D2

case $? in
0)
echo "NINO_DESKTOP ONLINE<BR>" >> /home/nino/test
;;
1)
echo "NINO_DESKTOP OFFLINE<BR>" >> /home/nino/test
;;
esac

cat /home/nino/cutup | grep 00:0F:B5:42:0C:D4

case $? in
0)
echo "CONTROL ONLINE<BR>" >> /home/nino/test
;;
1)
echo "CONTROL OFFLINE<BR>" >> /home/nino/test
;;
esac
rm -f /home/nino/cutup
rm /home/nino/macs


```

the php code im using is:

execute the script and output it to /home/nino/test

```

<?php  
  $test = shell_exec('/bin/online_users_for_site');
  echo($test);
?>

```

then echo out the file:

```

<?php  
  $data = shell_exec('cat /home/nino/test');
  echo($data);
?>

```

When i execure the script on the server directly it runs and generates the file with the info.  however when i try to do it via the php i get nothing.  Possible file permissions? is there a better way to execute commands on a server and display the output

Thanks for any help 

nino

---

### Post by ninocass on 2006-12-02
had a further look at the script and it seem when the website calls the wget part it dosent execute, any ideas?

cheers

Nino

---

### Post by duff on 2006-12-02
> **ninocass said:**
> had a further look at the script and it seem when the website calls the wget part it dosent execute, any ideas?

cheers

Nino

I know nothing of PHP, but maybe the $PATH variable isn't set.  Try /usr/bin/wget instead.

---

### Post by ninocass on 2006-12-02
yea it needed an absolute path also the files were being make under the user www-data so i made a temp dir chown'ed it to www-data and put all the the files needed in there

working a treat now :D

---

### Post by adamkane on 2006-12-02
Also:
[http://www.php.net/manual/en/function.shell-exec.php](http://www.php.net/manual/en/function.shell-exec.php)

---

