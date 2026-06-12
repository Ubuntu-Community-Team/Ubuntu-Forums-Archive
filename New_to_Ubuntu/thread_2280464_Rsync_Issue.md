---
title: "Rsync Issue"
date: 2015-05-30
forum: New to Ubuntu
---

### Post by john_smith33 on 2015-05-30
I just set up a new ubuntu server and I am trying to move my media files from my openmediavault server. When I run rsync it downloads folders but they are empty. Here is command I tried. Im sure that I missing something just not sure what it is.

```
sudo -u root rsync -avhzSP --stats @192.168.1.10:/media/57f04f97-0693-4f14-a522-9b89d1b94cb1/HQMovies/Downloads_partial /storage/allaccess/secured/
``` 


This is the result
```
Number of files: 5 (dir: 3, link: 2)Number of created files: 5 (dir: 3, link: 2)
Number of regular files transferred: 0
Total file size: 364 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 745
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 29
Total bytes received: 771


sent 29 bytes  received 771 bytes  69.57 bytes/sec
total size is 364  speedup is 0.46



```

Thanks in advance

---

### Post by papibe on 2015-05-30
Hi john_smith33.

A couple of thoughts:

You don't have to use the -u option if you want to be root with sudo.

The format for the user and host is not quite right. If you want to connect using the same name as the local current user, just use the ip address, or host name. If you want to use another user, you use the format 'user@ip' or 'user@hostname'.

Does it makes any difference if you run it like this:
```
sudo rsync -avhzSP --stats 192.168.1.10:/media/57f04f97-0693-4f14-a522-9b89d1b94cb1/HQMovies/Downloads_partial /storage/allaccess/secured/
```
Regards.

---

### Post by john_smith33 on 2015-05-30
Same result. I have tried about fifty different combinations. I wish it would throw an error.

---

### Post by papibe on 2015-05-30
I believe you're using rsync over ssh, right?

Have you test the ssh connection with root?
```
user@localhost:~$ sudo -i
[sudo] password for user: 
root@localhost:~#

root@localhost:~# ssh 192.168.1.10
root@192.168.1.10's password: 
root@192.168.1.10:~#
root@192.168.1.10:~#
```
Is root enable for remote logins on the remote server? why? (not recommendable)

Regards.

---

### Post by john_smith33 on 2015-05-30
I am able to connect with root it actually created the folders on the remote server Its just the actual files that are not transferring.

```

Number of files: 5 (dir: 3, link: 2)Number of created files: 5 (dir: 3, link: 2)
Number of regular files transferred: 0
Total file size: 364 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 745
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 29
Total bytes received: 771


sent 29 bytes  received 771 bytes  69.57 bytes/sec [COLOR=#000000][FONT=Ubuntu Mono]total size is 364  speedup is 0.46[/FONT][/COLOR]
```

---

### Post by SeijiSensei on 2015-05-30
I've never used any other options except "-av" or "-avz" if I was transferring over a low-bandwidth connection. If I ever had "sparse" files (-S), I didn't know it, and rsync never seemed to care either.

So start with "-av" and see how things go.

You are running this as root with sudo to avoid permission issues, yes?

---

### Post by john_smith33 on 2015-05-30
Yes I am running it as root. Same result with -av and -avz its just weird because it runs and does not give an error.

---

### Post by SeijiSensei on 2015-05-30
You sure those files in "Downloads_partial" aren't "hidden" with a leading dot?  Maybe they're already there, but not visible unless you use "ls -a"?

Try deleting the target directory then running rsync so it will be forced to transfer everything again.

---

### Post by Keith_Helms on 2015-05-31
Leave off the @ (at sign).   That is only used if you specify a user name and you don't need to prefix the hostname with it if there's no user name specified.

Never mind.   It looks like you already tried that.

Have you tried using option r for recursing into directories?

---

### Post by HermanAB on 2015-05-31
Do you really want to download the partials directory?  That probably has nothing in it, so rsync behaves correctly.

Bear in mind that rsync is ancient.  It doesn't have bugs anymore.  Whatever problems you encounter are your own doing.

---

### Post by john_smith33 on 2015-05-31
I'm sure it is user error. I'm just here to try and find out what i'm doing wrong. It is not really partial downloads it was just the smallest folder to test.

---

### Post by Keith_Helms on 2015-06-01
Have you tried the -r option?

---

### Post by papibe on 2015-06-03
Let's try to do a test locally on the remote server. ssh onto the server:
```
ssh root@192.168.1.10
```
Then on the server itself create a directory:
```
mkdir /tmp/secured
```
And then do a 'dry run' (not actually do the transfer, but print all messages as if it were):
```
rsync -avP --stats  **--dry-run** /media/57f04f97-0693-4f14-a522-9b89d1b94cb1/HQMovies/Downloads_partial /tmp/secured/
```
Let us know if that is transferring the files.

Regards.

---

### Post by john_smith33 on 2015-06-03
Thanks

Here is the result 

```
root@kristina:~# rsync -avP --stats  --dry-run /media/57f04f97-0693-4f14-a522-9b89d1b94cb1/HQMovies/Downloads_partial /tmp/secured/sending incremental file list
Downloads_partial/
Downloads_partial/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION/
Downloads_partial/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION.mkv -> /media/21351bd5-5e08-4f59-aa7e-8f8387c60666/.greyhole/HQMovies/Downloads_partial/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION.mkv
Downloads_partial/Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE/
Downloads_partial/Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE/Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE.mkv
Downloads_partial/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION/
Downloads_partial/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION.mkv -> /media/57f04f97-0693-4f14-a522-9b89d1b94cb1/.greyhole/HQMovies/Downloads_partial/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION.mkv


Number of files: 7
Number of files transferred: 1
Total file size: 1586659167 bytes
Total transferred file size: 1586658803 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 911
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 949
Total bytes received: 37


sent 949 bytes  received 37 bytes  1972.00 bytes/sec
total size is 1586659167  speedup is 1609187.80 (DRY RUN)
root@kristina:~# 



```

---

### Post by papibe on 2015-06-03
OK, thanks. So it seems to work.

Now on the client machine, ***carefully*** remove what you may have transferred already:
```
sudo rm -rf /storage/allaccess/secured/*
```
And then try again the original transfer:
```
sudo rsync -avP --stats --dry-run 192.168.1.10:/media/57f04f97-0693-4f14-a522-9b89d1b94cb1/HQMovies/Downloads_partial /storage/allaccess/secured/
```
What would be the output of that?

If that seems to work, you could try without the **--dry-run** to actually do the transfer.

Let us know how it goes.
Regards.

---

### Post by john_smith33 on 2015-06-03
bizarre


Only the folders and one file transfered "Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE/Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE.mkv" the other 2 folders are empty.


```
john@john:/storage/allaccess/secured$ sudo rsync -avP --stats 192.168.1.10:/media/57f04f97-0693-4f14-a522-9b89d1b94cb1/HQMovies/Downloads_partial /storage/allaccess/secured/                   root@192.168.1.10's password:                                                                                                                                                                   
receiving incremental file list                                                                                                                                                                 
Downloads_partial/                                                                                                                                                                              
Downloads_partial/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION/                                                                                                                                
Downloads_partial/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION.mkv -> /media/21351bd5-5e08-4f59-aa7e-8f8387c60666/.greyhole/HQMovies/Downloads_partial/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION/Modern.Family.S06E23.720p.HDTV.X264-DIMENSION.mkv                                                                                           
Downloads_partial/Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE/
Downloads_partial/Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE/Sons.of.Anarchy.S04E14.720p.HDTV.x264-IMMERSE.mkv
  1,586,658,803 100%   24.10MB/s    0:01:02 (xfr#1, to-chk=1/7)
Downloads_partial/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION/
Downloads_partial/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION.mkv -> /media/57f04f97-0693-4f14-a522-9b89d1b94cb1/.greyhole/HQMovies/Downloads_partial/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION/The.Odd.Couple.2015.S01E12.720p.HDTV.X264-DIMENSION.mkv


Number of files: 7 (reg: 1, dir: 4, link: 2)
Number of created files: 7 (reg: 1, dir: 4, link: 2)
Number of regular files transferred: 1
Total file size: 1,586,659,167 bytes
Total transferred file size: 1,586,658,803 bytes
Literal data: 1,586,658,803 bytes
Matched data: 0 bytes
File list size: 921
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 52
Total bytes received: 1,586,853,477


sent 52 bytes  received 1,586,853,477 bytes  19,234,588.23 bytes/sec
total size is 1,586,659,167  speedup is 1.00
john@john:/storage/allaccess/secured$ 



```

---

### Post by john_smith33 on 2015-06-03
Thanks for your help but I just had a thought. Maybe the files are not there. The server is running grayhole and I am checking the directory with smb so it looks like the files are in one location. My next question would be possible to rsync a grayhole share instead of the exact directory. I cant wait to use MHDDFS and snap raid on my new server.

---

