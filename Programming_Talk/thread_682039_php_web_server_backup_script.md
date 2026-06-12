---
title: "php web server backup script"
date: 2008-01-29
forum: Programming Talk
---

### Post by matthew on 2008-01-29
I have several websites. In each of them, I use a variation of the following script to perform a nightly backup of the site. The script is kept in my server's home directory, one level above public_html, and called up via cron. I've been using this for a long time and it works well.

[php]<?php
$emailaddress = "myemail@address.com";
$target = "/home/".get_current_user()."/backup.".date(d).".tar.gz";
if (file_exists($target)) unlink($target);
system("tar --create --preserve --gzip  --file=".$target." ~/public_html ~/mail",$result);
$size = filesize($target);
switch ($size) {
  case ($size>=1048576): $size = round($size/1048576) . " MB"; break;
  case ($size>=1024);    $size = round($size/1024) . " KB"; break;
  default:               $size = $size . " bytes"; break;
}
$message = "The website backup has been run.\n\n";
$message .= "The return code was: " . $result . "\n\n";
$message .= "The file path is: " . $target . "\n\n";
$message .= "Size of the backup: " . $size . "\n\n";
$message .= "Server time of the backup: " . date(" F d h:ia") . "\n\n";
mail($emailaddress, "Website Backup Message" , $message, "From: Website <>"); 
?> [/php]One of my sites has lots of graphic images in a specific directory, and it is getting to be quite big. I have the images backed up using another method, and would like to exclude that one directory.

Would I just change this line to read[php]system("tar --create --preserve --gzip  --file=".$target." --exclude=~/backupexclude ~/public_html ~/mail",$result);[/php]I'm familiar enough with tar to be pretty sure that should do the trick...am I fooling myself or is it really that easy?

---

### Post by matthew on 2008-01-30
This is a quick followup. I tested it last night and the modification worked well. I also tested another idea (that I picked up by reading the [GNU man page for tar]("http://www.gnu.org/software/tar/manual/tar.html#SEC_Top")) that is even cooler. You can list any number of directories in a test file, one directory per line, and then have your script pull the directories to exclude from that file. Pretty slick!

Here's the new line[php]system("tar --create --preserve --gzip  --file=".$target." --exclude-from=~/backupexcludefilename ~/public_html ~/mail",$result);  [/php]Then you create a file named "backupexcludefilename" in this example, with contents like this```
~/foldertoexclude1
~/directory/subdirectorytoexclude1
~/skipthis
```and so on.

Have fun!

---

### Post by LaRoza on 2008-01-30
Neat. 

(I don't backup my websites, though, because I develop them on my local server and test them there then upload)

---

### Post by matthew on 2008-01-30
> **LaRoza said:**
> Neat. 

(I don't backup my websites, though, because I develop them on my local server and test them there then upload)This does an automatic backup for my site each day, which I can then download (along with my automatic mysql backups, but that is another thread...).

I have some business sites, where backups are more important than on my fun sites, but I back them all up.

---

### Post by LaRoza on 2008-01-30
> **matthew said:**
> This does an automatic backup for my site each day, which I can then download (along with my automatic mysql backups, but that is another thread...).

I have some business sites, where backups are more important than on my fun sites, but I back them all up.

I understand. I have one :)

See my sig link if you are interested. Although I may seem mild mannered, I may have all sorts of porn in there.

(Shameless trying to get another visitor)

---

### Post by deuce868 on 2008-01-30
BackupPC ftw! 

Seriously, check out something that does dedicated backups like backuppc. I use that to run things nightly. Between that and
[http://members.lycos.co.uk/wipe_out/automysqlbackup/](http://members.lycos.co.uk/wipe_out/automysqlbackup/)

Things are backed up pretty nicely and you can do all kinds of tricks. restore files from a web interface and get the backups off the server somewhere off site.

---

