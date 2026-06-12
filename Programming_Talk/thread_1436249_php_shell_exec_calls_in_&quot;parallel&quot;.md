---
title: "php shell_exec calls in &quot;parallel&quot;"
date: 2010-03-22
forum: Programming Talk
---

### Post by Sycron on 2010-03-22
I have something like that
php function```
function is_online($ip){ $o = 0;
 $o = shell_exec("/var/pi/checkip ".$ip);
 if($o == '') $o = 0;
 if ($o == 0) echo '<img src="css/images/blocked.png" alt="" width="11" height="11"/>';
   else if((int)$o == 1) echo '<img src="css/images/ok.png" alt="" width="11" height="11"/>';
}
```

checkip script```
if ping -c 1 -W 2 $1 > /dev/null; then
echo "1"
else
echo "0"
fi

```and the procedure in action```
while there are ips in database {echo $ip; $is_online($ip);} 
```

If all the pings to ips are working the page instantly loads, but if there are any dead hosts a delay of 2sec/ip is observed. Is there a way to make those shell_exec to run in parallel? so the biggest load time to be the ping timeout(2sec in this case).

Any help is appreciated. Thanks.

---

