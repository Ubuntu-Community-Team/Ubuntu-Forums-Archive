---
title: "php file upload script help"
date: 2013-12-30
forum: Programming Talk
---

### Post by Habitual on 2013-12-30
I have some legacy php coded files that upload a file to the webserver.

The script "sort of" works now, but does not upload to the correct directory.

[PHP]if(!empty($_FILES['fileToUpload']['name'])){
$filename = sanitize_file_name($_FILES['fileToUpload']['name']);
$savePath = 'lvUTmp';
if(!file_exists(ABSPATH . $savePath)){
mkdir($savePath, 0703, true);
}[/PHP] 
is the relevant snippet.

It gets put in /var/www/html/domain instead.

[This]("http://stackoverflow.com/questions/1960180/abspath-or-file") says "Also, using the WordPress internal constants (such as ABSPATH) is not recommended"
so since I'd like to avoid that, I need to change it.

Most of the guts of the script can be seen over [here...]("https://www.linuxquestions.org/questions/programming-9/php-file-upload-help-with-code-4175489293/#post5087606")

Thank you.

---

### Post by SeijiSensei on 2013-12-31
There are two file locations involved here.  One is the temporary directory specified in /etc/php.ini or overriden by [upload_tmp_dir](http://www.php.net/manual/en/ini.core.php#ini.upload-tmp-dir):

```

ini_set('upload_tmp_dir','/path/to/some/directory');

```

Usually you want to move this file to a permanent location.  For that PHP offers the [move_uploaded_file()]("http://www.php.net/manual/en/function.move-uploaded-file.php") function.

Naturally both of these directories must be writable by the server user, www-data.

---

### Post by Habitual on 2013-12-31
> **SeijiSensei said:**
> There are two file locations involved here.  One is the temporary directory specified in /etc/php.ini or overriden by [upload_tmp_dir]("http://www.php.net/manual/en/ini.core.php#ini.upload-tmp-dir"):

```

ini_set('upload_tmp_dir','/path/to/some/directory');

```

Usually you want to move this file to a permanent location.  For that PHP offers the [move_uploaded_file()]("http://www.php.net/manual/en/function.move-uploaded-file.php") function.

Naturally both of these directories must be writable by the server user, www-data.

Thanks SeijiSensei;
I have already set (after posting this)
 ```
upload_tmp_dir = '/var/www/html/domain/lvUTmp';
``` in /etc/php.ini and bounced httpd.

```
ls -ld lvUTmp
drwx-----x. 2 apache apache 4096 Dec 31 07:05 lvUTmp/
```
and 
```
stat -c%a lvUTmp/
701
```

Where should I attempt to use
```
ini_set('upload_tmp_dir','/path/to/some/directory');
```?

Thanks.

---

### Post by SeijiSensei on 2013-12-31
If you make the change in php.ini, you don't need to use ini_set().  That function allows you to override  configuration settings on the fly.

---

### Post by Habitual on 2014-01-02
Update:
```
curl_setopt($Curl_Session, CURLOPT_URL, 'https://fileserver.domain.com:8443/FileServer/fileupload');
curl_setopt($Curl_Session, CURLOPT_POSTFIELDS, $filename);
``` and *verboseOut.txt* now shows:
```
< HTTP/1.1 200 OK
< Server: Apache-Coyote/1.1
< Content-Length: 0
< Date: Thu, 02 Jan 2014 16:24:04 GMT
< 
* Connection #0 to host fileserver.domain.com left intact
* Closing connection #0
```

Still no file write on [noparse]fileserver.domain.com/FileServer/<user_name>[/noparse]

inching closer...

---

### Post by Habitual on 2014-01-02
well, it's working.
I never could get uploaded files into /var/www/html/domain/lvUTmp
but I can remove them from /var/www/html/domain/ using 
[PHP]unlink($filename);[/PHP] after they get copied to the remote tomcat FileServer/<user_name> resource. so it's mostly moot now.

Thanks!

---

