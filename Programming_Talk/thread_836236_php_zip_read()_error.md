---
title: "php zip_read() error"
date: 2008-06-21
forum: Programming Talk
---

### Post by dknife on 2008-06-21
I've been banging my head against a wall all morning on this. I've been searching around for hours trying to find a solution. I've moved a project from one server to another, and this used to work fine on the old server, which was Ubuntu 7. The new server is Ubuntu 8. The problem is this error:

Warning: zip_read() expects parameter 1 to be resource, integer given in /path/to/file/file.php on line 92

Everything I've read points to either a path or permissions problem. It is exactly the same path as the old server and I know the path is correct. I've tried messing with permissions, running as root etc. I've checked phpinfo and zip and zlib is enabled.

I can't see any difference in anything between the servers, other than one is running the latest version of Ubuntu. One is running php 5.2.3 and the new one is 5.2.4.

Anyone got any ideas of what I'm missing on the new server? Is there a package I might have installed on the old one not present on the new one yet?

---

### Post by supirman on 2008-06-21
That means that zip_open failed to open the file.  zip_open returns a resource on success, or an integer error number on failure.  To decipher the error code returned from zip_open, see [http://us.php.net/manual/en/function.zip-open.php#75840](http://us.php.net/manual/en/function.zip-open.php#75840)

This will help you diagnose the issue.  Or, just echo out the return value from zip_open, then we can figure out the error.

---

### Post by dknife on 2008-06-26
Actually I've worked out that this is in fact a bug in php 5.2 which occurs on zip files over 509 files on some 64bit systems :(

As soon as you remove most of the files down before 500 then it works fine.

The only updates i've managed to find on this issue is that it was suggested to try the latest 5.3 snapshot of php.

---

