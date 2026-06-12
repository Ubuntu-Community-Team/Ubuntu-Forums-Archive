---
title: "Script to download a file from an FTP server and upload it to an SFTP server."
date: 2023-12-05
forum: Programming Talk
---

### Post by WhiteTigerIT on 2023-12-05
I would like some advice on creating a script (to run on an Ubuntu server) that does these things:

[LIST=1]
[*]read a text file where there is a list of ft p://server/folder/file-name.tar.gz (The FTP server is always the same and I have the credentials).
[*]read the first line and launch the download.
[*]save/transfert this file on SFTP server (I have credentials) in a TMP_ZIP folder.
[*]unzip the file into the /folder1/file-name folder (the folder name is the same as the downloaded file).
[*]Delete the downloaded file from the TMP_ZIP folder
[*]Move on to reading the second line and thus launching the second download.
[/LIST]


I have these questions:

[LIST]
[*]I want to install as little as possible on the server, better if I can use what is already provided with the basic installation.
[*]what script to use? Python? Bash?
[*]possibly transfer the file directly from the ftp server to the sftp server without having to temporarily download it to the intermediate server (the one that launches the script, so to speak)
[/LIST]


I have credentials to access both the ftp and sftp server, but I can't run the script on either.


Thanks in advance for the advice.

---

### Post by TheFu on 2023-12-05
Do you have ssh access to both systems?

---

### Post by jimmyrus on 2023-12-05
> **WhiteTigerIT said:**
> I would like some advice on creating a script (to run on an Ubuntu server) that does these things:

[LIST=1]
[*]read a text file where there is a list of ft p://server/folder/file-name.tar.gz (The FTP server is always the same and I have the credentials).
[*]read the first line and launch the download.
[*]save/transfert this file on SFTP server (I have credentials) in a TMP_ZIP folder.
[*]unzip the file into the /folder1/file-name folder (the folder name is the same as the downloaded file).
[*]Delete the downloaded file from the TMP_ZIP folder
[*]Move on to reading the second line and thus launching the second download.
[/LIST]


I have these questions:

[LIST]
[*]I want to install as little as possible on the server, better if I can use what is already provided with the basic installation.
[*]what script to use? Python? Bash?
[*]possibly transfer the file directly from the ftp server to the sftp server without having to temporarily download it to the intermediate server (the one that launches the script, so to speak)
[/LIST]


I have credentials to access both the ftp and sftp server, but I can't run the script on either.


Thanks in advance for the advice.
agree with thefu about using ssh for the whole thing, since that'll make things a breeze. You can do this with bash python perl or a ton of different languages. The
pseudo code would be a simple loop reading the file and running things based on that variable you read in. If it was me I'd download things and move them to an
archive folder on the local ubuntu server in case theres a need to resend later..you could do that manually without having to redownload something if it blows off.

you already got the sftp and ftp commands and there are tons of example scripts for python and bash for ftp and sftp. Doing the sftp keyswap means you won't even
need a password to upload, and can (dunno?) use scp instead of sftp, so your command line may just be something like scp /my/path/file user@othermachine:/remote/path
and that's it. also I'd ask about using ftp to start with since it's old junk and very insecure. Why can't you use sftp or scp on both systems?

---

### Post by WhiteTigerIT on 2023-12-06
The starting server is not mine and I do not have access to its backend, but only to the HTML pages.
I only have the public list of files downloadable via FTP. To be clear, from the WEB page the link is of the "ftp://" type.
I can download them freely with any tools, for example "Free Download Manager". With Filezilla, however, I can't because I would instead have to provide access parameters that are not public.

The arrival server is a hosting platform on an ISP. I could install a CMS like Joomla or Wordpress on it, but it seems like an unnecessary burden to me.
I can instead upload the files to a folder, but using SFTP.

The files I need to download are related to public lists, but compacted with TAR.GZ.
Which means that normally I would have to do a double unpacking by hand; I only need the final file.
Since the files are updated periodically, it makes no sense to do it manually.
For this reason I thought of a script that would take care of all the operations.

I have an Ubuntu VPS to launch it from, but I've also thought about launching it from my Xubuntu PC because the VPS is already stretched to the limit and I don't plan on replacing it until at least next spring.
If I launch it from the server I want to avoid installing anything else unless necessary.

Nor do I want to keep the files on my VPS, both for space reasons since I would leave the files uncompressed, but above all because since I also have to leave them public I don't want to worry about having to apply protections to avoid unauthorized access.
That's why I want to put them on a hosted folder, where there won't be anything else to protect.

---

### Post by TheFu on 2023-12-06
Thanks for the clarification.
You access to some files on someone else's computer. That access is only plain FTP. Nothing else.  
You want the files on a VPS that you own, manage.
The files are updated periodically - daily, monthly, yearly, doesn't matter.
The file names all have a known pattern.

Ok, so my solution would be to run a **wget** or **curl** script on the VPS to pull/update the files as often as you need. Daily, weekly, monthly are all trivial using "cron".  This would remove any need for the files to be placed on your local system or for that local system to be involved at all. K.I.S.S. in action.

I do something similar, every 4 hours to get IPTV schedule data.

```
#!/bin/bash
CACHE_DIR="/final/location/for/files"
wget -O $CACHE_DIR/outputfile.xml   https://i.xyz.ca/TV/us.m3u8

```
Simple when the filename doesn't change or a pattern isn't needed.  If a pattern is used, wget has the -A{pattern} option.

Say I know that all the files in the URL will match *high-quality.mp3" - then I'd use 
```
wget  -nd   -Ahigh-quality.mp3    https://i.xyz.ca/TV/
```
to get them and retain the filename in the current local directory.

Place your FTP login credentials into the ~/.netrc file.  It is a standard format used by FTP and wget will check it.

Or you can use **curl**.  There are thousands of examples of curl in use on the internet.

Sadly, curl and wget don't know if you have the file already, so they will download each again.  **rsync** would be better in that case, since it would only get changed data in each file or nothing if the file hasn't changed, but it requires ssh access. Too bad.

If you don't want these files on your VPS, don't use it. Put the script on your local workstation.

---

### Post by WhiteTigerIT on 2023-12-07
Thanks for your suggestions.
I'll do some tests right away

---

