---
title: "Making a screen shot from cron"
date: 2005-01-06
forum: Programming Talk
---

### Post by notos on 2005-01-06
i am making a scrtip that takes  a screen from your desktop conects to your FTP and uploads it an a thumb and youi know what it Works!!!!! ... but only when i run it when it is run by cron it gives me an errer "can not conect to X server" :(

i put the code here it is programed with PHP(Cli)


actualy te line that gives error is

import -window root $local_file

```

#!/usr/local/bin/php
<?php
##############################
#   (c) by notos | julianduenas@gmail.com    #
#   this Script is under the Gnu/GPL             #
##############################

# configuration
 $ftp_server = 'server.com';
 $ftp_port = 21;
 $ftp_user = 'user';
 $ftp_pass = 'pass';
 $ftp_dir = '/public_html/screens';
 # image type
 $ext = 'png';


 

# Edit this only if you know what are you doing  
 $local_file = "/tmp/current.$ext";
 $local_thumb = '/tmp/current_thumb.'.$ext;
 exec("import -window root $local_file");
 exec("convert -sample 25%x25% $local_file $local_thumb"); 
 
 $image = fopen($local_file, 'r');
 $image_thumb = fopen($local_thumb, 'r');
 
 $file = $ftp_dir.'/current.'.$ext;
 $file_thumb = $ftp_dir.'/current_thumb.'.$ext;
 
 $ftp_id = ftp_connect($ftp_server,$ftp_port) or die('error');
 $ftp_login = ftp_login($ftp_id,$ftp_user,$ftp_pass);
 
 
 function upload_current()
 {
  global $ftp_id,$image_thumb,$file_thumb,$image,$file,$local_file,$local_thumb; 
  if (ftp_fput($ftp_id, $file_thumb, $image_thumb, FTP_BINARY)) {
   echo "Successfully uploaded $file_thumb\n";
  } else {
   echo "There was a problem while uploading $file\n";
  }

  if (ftp_fput($ftp_id, $file, $image, FTP_BINARY)) {
   echo "Successfully uploaded $file\n";
  } else {
   echo "There was a problem while uploading $file\n";
  }
  unlink($local_file);
  unlink($local_thumb);
 }
 
 if (!file_exists('LOCAL'))
 {
  ftp_mkdir($ftp_id,$ftp_dir);
  ftp_mkdir($ftp_id,$ftp_dir."/archive");
  fopen('LOCAL','x');
  upload_current();
 }
 else
 {
  $time = date('Y-m-d-H_i_s');
  ftp_rename($ftp_id,$ftp_dir."/current.$ext",$ftp_dir."/archive/$time.$ext");
  ftp_rename($ftp_id,$ftp_dir."/current_thumb.$ext",$ftp_dir."/archive/".$time."_thumb.".$ext."");
  upload_current();
 }
ftp_close($ftp_id);
exit(0);
?>

```

---

### Post by 2fargon on 2005-01-06
Is it because your login times out or your screen locks after a certain amount of time of inactivity?

---

### Post by lordan on 2005-01-06
It's because the process doesn't have access to the DISPLAY environment variable.

---

### Post by #Greg on 2005-01-09
Couldn't you just do a shell script which takes a screen shot and uploads it to your FTP server? Then add it up cron, or is there a reason that you want it to be done via PHP?

---

### Post by duff on 2005-01-10
no idea how to do this, but it may be possible to connect to the gnome-panel-screenshot applet via bonobo and have that take the screenshot instead of using imagemagick.

---

### Post by Danilo on 2005-01-11
Just do what lordan suggested, call import something like:
```
DISPLAY=:0.0 import -window root ...
```
You might also need to add hostname there as well, and perhaps even go as far to xhost address of the computer script is running on (if not the same), but that's stretching it a bit, so check the documentation if that's what you want :)

---

