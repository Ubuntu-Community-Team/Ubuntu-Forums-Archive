---
title: "PHP $_POST variable help"
date: 2009-04-04
forum: Programming Talk
---

### Post by mvalviar on 2009-04-04
Forgive me if the answer is obvious yet I ask this question. I really can't figure it out. I'm new to php. I have this script ```

<form action="test1.php">
    <input type="text" name="name" />
    <input type="submit" />
</form>
```
The target is ```

<?php
if (empty($_POST['name'])) echo "You entered nothing";
else echo "Hello ".$_POST['name'];
?>
```

Why does it always say its empty?

---

### Post by s.fox on 2009-04-04
You are missing the method from the form tag.

```
 method = "POST"
```

---

### Post by TuXAPuK on 2009-07-19
Ai have some shame problem but my form is pretty fine

<form action="/" method="POST" enctype="multipart/form-data">[FONT=monospace]
[/FONT]<input type="text" name="galUser"><br>[FONT=monospace]
[/FONT] <input type="text" name="galPass"><br>[FONT=monospace]
[/FONT] <input type="submit" value="...">[FONT=monospace]
[/FONT]</form>

Firefox header debug dump :

QUERY :

POST / HTTP/1.1
....lalala...
Content-Type: multipart/form-data; boundary=---------------------------16423500210585
Content-Length: 400
-----------------------------16423500210585
Content-Disposition: form-data; name="galUser"

private
-----------------------------16423500210585
Content-Disposition: form-data; name="galPass"

home
-----------------------------16423500210585--

RESPONSE :

HTTP/1.x 200 OK
Connection: Keep-Alive
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Pragma: no-cache
Keep-Alive: timeout=15, max=100
Content-Length: 1398
Content-Type: text/html; charset=UTF-8
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
X-Powered-By: PHP/5.2.4-2ubuntu5.6
Date: Sun, 19 Jul 2009 18:19:14 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch


PHP script :
echo getenv('REQUEST_METHOD') .'<br>';
print_r( $_POST );

Says :
POST
Array()

Also :
file_get_contents('php://input');

Returns :[FONT=monospace]
[/FONT]-----------------------------228163169013162
Content-Disposition: form-data; name="galUser"

private
-----------------------------228163169013162
Content-Disposition: form-data; name="galPass"

home
-----------------------------228163169013162--



Ai do not understand where a problem...
On my notebook (win+app2+php5) this script work very fine...

---

### Post by TuXAPuK on 2009-07-20
**I will founded solution for my problem**
More information can be found in PHP post_max_size derective. if value larger than ram size - then script do not want create $_POST value...

---

