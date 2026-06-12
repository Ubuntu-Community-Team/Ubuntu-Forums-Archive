---
title: "Vsftpd from web browser"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by blx_286 on 2008-04-28
I have a Dapper server setup and it is only running OpenSSH and Vsftpd. I have vsftpd setup to not allow anonymous logins, all users must login. I would like to know if there is a way to access the server with a web browser instead of an ftp client? This is for client uploads and downloads, not for administration.

Thanks,
Tim

---

### Post by Monicker on 2008-04-28
> **blx_286 said:**
> I have a Dapper server setup and it is only running OpenSSH and Vsftpd. I have vsftpd setup to not allow anonymous logins, all users must login. I would like to know if there is a way to access the server with a web browser instead of an ftp client? This is for client uploads and downloads, not for administration.

Thanks,
Tim

Modern web browsers support accessing an ftp server via the ftp:// URI.  A username and password can also be specified.

Would that not be sufficient?

---

### Post by blx_286 on 2008-04-28
I was hoping there was a way to prompt the user for a login and password for the session. After reading your post, I found I can access the site with [ftp://mylogin@ftp.servername.com](ftp://mylogin@ftp.servername.com), but every time I go into a sub-directory, I have to edit the address and put my name back in.

Thanks,
Tim

---

### Post by blx_286 on 2008-04-29
I am trying to replace an ftp server that my predecessor had in place. The server has failed and will not even boot up, so I don't know what he had running but it was a Windows app. I have setup a Dapper FTP as a replacement, but the users are demanding the same interface. When they accessed the original FTP server with Internet Explorer, they were prompted for a login and password.

Can I do something like this with Apache and if so, is there a how-to? Or can someone recommend an open source solution for this?

Thanks,
Tim

---

### Post by blx_286 on 2008-04-30
After checking around on google, I found what I am looking for is a web based ftp client. I found one at [http://freshmeat.net/projects/net2ftp/]("http://freshmeat.net/projects/net2ftp/") but it hasn't been updated in over a year. Is anyone using something similar?

Thanks,
Tim

---

