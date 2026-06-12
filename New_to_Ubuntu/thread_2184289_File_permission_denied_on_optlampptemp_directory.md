---
title: "File permission denied on /opt/lampp/temp/ directory"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by Tanmay_Das on 2013-10-28
Hi there, never really thought I'll ever have to post a new thread on  Ubuntu Forum for a solution. Because every time I face a problem on  Ubuntu, I just Google it and find that it's already [solved] :smile:  by someone else on ubuntuforum. Ubuntu Forum is really an awesome  community that makes Linux-life much easier. I'd like to express my  deepest gratitude to you guys who've built this platform for years.

Well, now the real problem. I am a PHP learner. I use Netbeans and Xampp  on my Ubuntu 12.04.3 LTS.  Everything was fine. But today I was trying  PHP File Upload.

The temporary folder path in php.ini file is: ```
upload_tmp_dir="/opt/lampp/temp/"
```

And the folder where the uploaded file is supposed to be moved:  ```
"/opt/lampp/htdocs/PHPUpload/upload"
``` Where PHPUpload is my  netbeans project directory.

My php file:
[PHP]<?php
$allowedExts = array("gif", "jpeg", "jpg", "png");
$temp = explode(".", $_FILES["file"]["name"]);
$extension = end($temp);
if ((($_FILES["file"]["type"] == "image/gif")
|| ($_FILES["file"]["type"] == "image/jpeg")
|| ($_FILES["file"]["type"] == "image/jpg")
|| ($_FILES["file"]["type"] == "image/pjpeg")
|| ($_FILES["file"]["type"] == "image/x-png")
|| ($_FILES["file"]["type"] == "image/png"))
&& ($_FILES["file"]["size"] < 2000000)
&& in_array($extension, $allowedExts))
  {
  if ($_FILES["file"]["error"] > 0)
    {
    echo "Return Code: " . $_FILES["file"]["error"] . "<br>";
    }
  else
    {
    echo "Upload: " . $_FILES["file"]["name"] . "<br>";
    echo "Type: " . $_FILES["file"]["type"] . "<br>";
    echo "Size: " . ($_FILES["file"]["size"] / 1024) . " kB<br>";
    echo "Temp file: " . $_FILES["file"]["tmp_name"] . "<br>";

    if (file_exists("upload/" . $_FILES["file"]["name"]))
      {
      echo $_FILES["file"]["name"] . " already exists. ";
      }
    else
      {
      move_uploaded_file($_FILES["file"]["tmp_name"],
      "/opt/lampp/htdocs/PHPUpload/upload/" . $_FILES["file"]["name"]);
      echo "Stored in: " . "upload/" . $_FILES["file"]["name"];
      }
    }
    
  }
else
  {
  echo "Invalid file";
  }
?> [/PHP]
When I upload the file, the following errors occur:
```

Upload: ProPic.jpg
Type: image/jpeg
Size: 744.9169921875 kB
Temp file: /tmp/phpabFdzH

**Warning**:  move_uploaded_file(/opt/lampp/htdocs/PHPUpload/upload/ProPic.jpg): failed to open stream: Permission denied in **/opt/lampp/htdocs/PHPUpload/up.php** on line **32**

**Warning**:  move_uploaded_file(): Unable to move '/tmp/phpabFdzH' to '/opt/lampp/htdocs/PHPUpload/upload/ProPic.jpg' in **/opt/lampp/htdocs/PHPUpload/up.php** on line **32**
Stored in: upload/ProPic.jpg
```
Please notice that, the 2nd warning message says, Unable to move  '/tmp/phpabFdzH' ("/opt/lampp/tmp/phpabFdzH"), which means it is  considering "/tmp/" as the temporary directory. Eventhough the temp  directory path defined in php.ini is: "/opt/lampp/temp/". Now this is  messed up because of me. When I found that the /temp directory is having  some problems with permission, I created a new one called /tmp and  updated the php.ini file with new path (simply erased 'e' from 'temp').  And it didn't work. Then I googled and found some bash commands to  change the permissions. And I think I messed up my file permissions.  Then I re-edited php.ini file and changed the path to /temp again. But  it is still taking the /tmp folder as the temporary folder even after  I've deleted the /tmp folder. Here is a screenshot of the commands ran  by me.
[IMG]http://img17.imageshack.us/img17/4324/cpz2.png[/IMG]

I've submitted all the information I have. Those chmod/chown commands were the last action performed by me.

Summary:
1) I expect my /temp directory to work as it should
2) My files should successfully be moved to the destination folder: /opt/lampp/htdocs/PHPUpload/upload/

Any help? And sorry for any mistake. This is my first post :(

---

### Post by whitesmith on 2013-10-28
Hi and welcome, **Tanmay_Das**! By default Ubuntu gives only read permission to a user oiutside $HOME. You would have to give yourself the necessary permissions in "/opt/lampp/htdocs/PHPUpload/upload" because that is outside /$HOME.

---

### Post by sammiev on 2013-10-28
```
sudo -i
```

will give you root access.

---

### Post by Tanmay_Das on 2013-10-28
Thank you for your kind response, whitesmith. I have uninstalled XAMPP and reinstalled it. I run netbeans as "tanmay" (not root). And I have no access to the /opt/lampp directory as a non-root user. I am seeing lock icons all over. Now I need to give the "/opt/lampp/htdocs" directory read write permission for user tanmay so that I can create new projects from netbeans directly. And what permission should I give to the folder "/opt/lampp/temp" in order to make my upload script work?

---

### Post by whitesmith on 2013-10-28
This is a bit over the top, but try giving that directory full permissions r+w+x. If that won't do it, nothing will! I know nothing about this program, but I'm wondering if it can be configured with user-accessible directories in specified locations. If it can, put them somewhere inside $HOME and you won't have to worry. Good luck!

---

