---
title: "Another PHP issue, $_GET and $_FILES"
date: 2007-03-29
forum: Programming Talk
---

### Post by lamalex on 2007-03-29
I need to be able to pass data through a url to $_FILES. However $_FILES will only receive $_POST data and I cannot send $_POST through a URL. Does anyone know a work around to this? I tried 
```

$uploadedfile=$_GET['uploadedfile'];
$target_path = '/var/www/virtual/acetechgroup.com/noc/htdocs/uploads/';
$file = $target_path . basename($_FILES[$uploadedfile]['name']);
echo $uploadedfile;

echo '<pre>';
if(move_uploaded_file($_FILES[$uploadedfile]['tmp_name'],$file)) {
        echo "The file has been uploaded \n";
}

```

that's the relevant code if needed. thanks for your help everyone, I'm learning :)

---

### Post by Frosty Cold Drink on 2007-03-29
> **Iamalex said:**
> I need to be able to pass data through a url to $_FILES. However $_FILES will only receive $_POST data and I cannot send $_POST through a URL. Does anyone know a work around to this? I tried 
```

$uploadedfile=$_GET['uploadedfile'];
$target_path = '/var/www/virtual/acetechgroup.com/noc/htdocs/uploads/';
$file = $target_path . basename($_FILES[$uploadedfile]['name']);
echo $uploadedfile;

echo '<pre>';
if(move_uploaded_file($_FILES[$uploadedfile]['tmp_name'],$file)) {
        echo "The file has been uploaded \n";
}

```

that's the relevant code if needed. thanks for your help everyone, I'm learning :)
$_FILES is for info about files uploaded in the request only. If your not POSTing, chances are your file isn't going to be uploaded.

Why do you need to use GET instead of POST? If I knew why perhaps I could think of a decent workaround.

---

### Post by lamalex on 2007-03-29
this is the scenario, a clients domain contoller scans its network for client machine names and IP addresses, it dumps each data set into a text file, 1 text file of client names, one textfile of IP addreses, and a static text file containing it's own name. a cron script goes off once a day that calls my webpage mywebpage.com/autoserverclient.php?clientname=client.text?clientip=clientip.txt?servername=servername.txt

that calls a bunch of functions that update our local DNS that is inside a mysql database.

---

### Post by Frosty Cold Drink on 2007-03-29
> **Iamalex said:**
> this is the scenario, a clients domain contoller scans its network for client machine names and IP addresses, it dumps each data set into a text file, 1 text file of client names, one textfile of IP addreses, and a static text file containing it's own name. a cron script goes off once a day that calls my webpage mywebpage.com/autoserverclient.php?clientname=client.text?clientip=clientip.txt?servername=servername.txt

that calls a bunch of functions that update our local DNS that is inside a mysql database.

So what you really want then is the DC to tell some code on your web server that it has updated its data. You need to make those files accessable to your web server somehow. Either you can make the data on the DC accessable to your web site somehow and use PHP to open those files remotely or download them and open them. That, or the DC can push the files to the web server.

If you do the former, PHPs fopen wrappers will let you open the file with regular file i/o routines, even though the files are stored remotely.

---

