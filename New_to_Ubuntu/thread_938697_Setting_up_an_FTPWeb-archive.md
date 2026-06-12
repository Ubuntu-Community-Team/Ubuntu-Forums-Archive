---
title: "Setting up an FTP/Web-archive"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Soulnoise on 2008-10-05
Hello!

Pardon me if I picked the wrong forum for this, but since I am absolute beginner in need of help...

See, recently I've come to be in need of a way to share a great deal of photos and other files with a group of other people in a fast way.

Now now, my first way out would be to set up a small torrent tracker in either uTorrent or Azureus, but many of those people don't use Bittorrent, the other way out would be to simply use Filehosts but I have way too many files for that.


So I decided to google around a bit and found some info about vsftpd,
how to install it and how to set it up.

This is where the problematic part begins, I have no idea how to set it up so it fits my needs :(


What I want to set up is one of these archives (y'know, /index pages?) that can be accessed through a browser after supplying a username + password, and the content of this archive would be some specific shared folder on my system. The web-access would be read-only, of course.

Another thing I'd like to achieve is to make it able for others to upload stuff from their computer through some ftp-client to their own assigned folders on my computer, or something like that. I know this is possible, err, at least I think it is -- but if you think I shouldn't meddle with that kind of sorcery then I guess I can live without that.

Help would be appreciated, if you can be arsed :(

---

### Post by jakev383 on 2008-10-05
> **Soulnoise said:**
> Hello!

Pardon me if I picked the wrong forum for this, but since I am absolute beginner in need of help...

See, recently I've come to be in need of a way to share a great deal of photos and other files with a group of other people in a fast way.


So I decided to google around a bit and found some info about vsftpd,
how to install it and how to set it up.

This is where the problematic part begins, I have no idea how to set it up so it fits my needs :(


What I want to set up is one of these archives (y'know, /index pages?) that can be accessed through a browser after supplying a username + password, and the content of this archive would be some specific shared folder on my system. The web-access would be read-only, of course.

Another thing I'd like to achieve is to make it able for others to upload stuff from their computer through some ftp-client to their own assigned folders on my computer, or something like that. I know this is possible, err, at least I think it is -- but if you think I shouldn't meddle with that kind of sorcery then I guess I can live without that.

Help would be appreciated, if you can be arsed :(

You're looking at 2 different things here.  Set the FTP up, and then set up Apache to allow access to the folder. To password protect, you'll need to read up on how to create a .htaccess file for AUTH. I believe Apache is now defaulted to show a directory listing of there is no index.html file, but that is easy to do if it is not.  
In vsftpd, create a user account (the FTP username) and give that user the homedir of the picture share.  Make sure in vsftpd to jail the user to their homedir or they'll browse your whole system.
At this point, you'll have a server where you can log in via FTP to a directory and upload files.  Users browsing to it from a web browser will now (after entering a user/pass) be able to view a directory listing of the pictures (the listing is generated on the fly, so if you add new pictures just hit the reload button in your browser to see them).
That should at least get you started in the right direction.

---

### Post by Soulnoise on 2008-10-05
> **jakev383 said:**
> You're looking at 2 different things here.  Set the FTP up, and then set up Apache to allow access to the folder. To password protect, you'll need to read up on how to create a .htaccess file for AUTH. I believe Apache is now defaulted to show a directory listing of there is no index.html file, but that is easy to do if it is not.  
In vsftpd, create a user account (the FTP username) and give that user the homedir of the picture share.  Make sure in vsftpd to jail the user to their homedir or they'll browse your whole system.
At this point, you'll have a server where you can log in via FTP to a directory and upload files.  Users browsing to it from a web browser will now (after entering a user/pass) be able to view a directory listing of the pictures (the listing is generated on the fly, so if you add new pictures just hit the reload button in your browser to see them).
That should at least get you started in the right direction.

I think I'll manage that. 

Thanks. :]

---

