---
title: "'grep' results of CURL response using PHP"
date: 2015-08-02
forum: Programming Talk
---

### Post by jamal13579 on 2015-08-02
I am sure that this is on the dumb end of the spectrum but I have been trawling the internet for hours and I can't get it to work (I really need to brush up (read: do the 101) on regex! Any help from you guys very much appreciated.

I am trying to migrate the following shell command to PHP:

```
curl  -s "http://localhost:80/balancer-manager" | grep "http"
```

This returns 5 lines:
```
<td><a href="/balancer-manager?b=localhost_cluster1&w=http://localhost:8080&nonce=3abe47c9-f724-4fdb-9e9c-0c91aa3e1f92">http://localhost:8080</a></td><td>69be0093449f0252bebabf73014df23f_server1_1</td><td></td><td>1</td><td>0</td><td>Ok</td><td>74</td><td> 40K</td><td> 15K</td></tr>
<td><a href="/balancer-manager?b=localhost_cluster2&w=http://localhost:8180&nonce=3abe47c9-f724-4fdb-9e9c-0c91aa3e1f92">http://localhost:8180</a></td><td>69be0093449f0252bebabf73014df23f_server2_1</td><td></td><td>1</td><td>0</td><td>Ok</td><td>0</td><td>  0 </td><td>  0 </td></tr>
<td><a href="/balancer-manager?b=localhost_cluster00&w=http://localhost:7080&nonce=3abe47c9-f724-4fdb-9e9c-0c91aa3e1f92">http://localhost:7080</a></td><td>69be0093449f0252bebabf73014df23f_server2_1</td><td></td><td>1</td><td>0</td><td>Ok</td><td>0</td><td>  0 </td><td>  0 </td></tr>
<td><a href="/balancer-manager?b=localhost_singleton1&w=http://localhost:8080&nonce=3abe47c9-f724-4fdb-9e9c-0c91aa3e1f92">http://localhost:8080</a></td><td></td><td></td><td>1</td><td>0</td><td>Ok</td><td>0</td><td>  0 </td><td>  0 </td></tr>
<td><a href="/balancer-manager?b=localhost_singleton2&w=http://localhost:8180&nonce=3abe47c9-f724-4fdb-9e9c-0c91aa3e1f92">http://localhost:8180</a></td><td>69be0093449f0252bebabf73014df23f_server2_1</td><td></td><td>1</td><td>0</td><td>Ok</td><td>0</td><td>  0 </td><td>  0 </td></tr>
```

I then strip this and do some stuff with it. At the moment I am calling shell_exec to perform this but I want to migrate it all over to PHP. This is what I have at the moment but it doesn't work:

[PHP]$url = "$protocol://$host:$port/balancer-manager";
$ch = curl_init();
curl_setopt($ch,CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_TIMEOUT, '3');
curl_setopt($ch,CURLOPT_SSL_VERIFYPEER, false);
$result = curl_exec($ch);
curl_close($ch);
$result = preg_match('/http/g', $result);
print_r($result);[/PHP]

Any help very much appreciated.

Chris

---

### Post by SeijiSensei on 2015-08-02
"It doesn't work" isn't enough to diagnose the problem.  What specifically happens? Are there any entries in /var/log/apache2/error.log?

Is $result a scalar or, I suspect, an array?  If the latter, then you'd need:
```
$result = curl_exec($ch);
curl_close($ch);
foreach ($result as $line) {
     $res2=preg_match('/http/g', $line);
     print_r($res2);  
}

```

---

### Post by jamal13579 on 2015-08-02
Yes, the results come out as an array and after having a little play I realised that each element of the array was an individual character! Well, I decided that I didn't want to go down that route but I have found what I think is a somewhere-just-past-half-way-there solution:

[PHP]$url = "$protocol://$host:$port/balancer-manager";
$ch = curl_init();
curl_setopt($ch,CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_TIMEOUT, '3');
curl_setopt($ch,CURLOPT_SSL_VERIFYPEER, false);
$result = curl_exec($ch);
curl_close($ch);
$rand = rand(0,1000);
$file = "/tmp/file_$rand";
file_put_contents("$file",$result);
$output = shell_exec("cat $file | grep http");
$results = preg_split("#[\r\n]+#", trim($output));
unlink($file);[/PHP]

This gives me the same behavior but while it removes the shell_exec for curl I'm still doing shell calls to get the data in the way I need it.

Will mark as solved because I am happy enough with the result. 

Thanks for your help :)

---

