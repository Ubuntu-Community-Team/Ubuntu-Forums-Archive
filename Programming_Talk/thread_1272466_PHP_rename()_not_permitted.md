---
title: "PHP rename() not permitted"
date: 2009-09-22
forum: Programming Talk
---

### Post by gencha on 2009-09-22
I am trying to move files in PHP via rename(). The files themselves belong to the group Apache is in (www-data) and the target directory is most definitely writable by Apache as well.
Yet when I try to rename(), I get the following error:
```
WARNING: rename(/home/frontend/uploadclip.xml,/var/media/45ecfe0fb82968cd0244666d3b92ac4a2658d844) [<a href='function.rename'>function.rename</a>]: Operation not permitted in /var/www/admin/uploadAddToPool.php on line 55
```

So, to determine if access rights might be the problem here, I replace the rename() call with a system( "mv .." ); call and this works flawlessly.

I would like to avoid using system() calls but I also have no clue why rename() would fail in this scenario.

---

### Post by Arndt on 2009-09-22
> **gencha said:**
> I am trying to move files in PHP via rename(). The files themselves belong to the group Apache is in (www-data) and the target directory is most definitely writable by Apache as well.
Yet when I try to rename(), I get the following error:
```
WARNING: rename(/home/frontend/uploadclip.xml,/var/media/45ecfe0fb82968cd0244666d3b92ac4a2658d844) [<a href='function.rename'>function.rename</a>]: Operation not permitted in /var/www/admin/uploadAddToPool.php on line 55
```

So, to determine if access rights might be the problem here, I replace the rename() call with a system( "mv .." ); call and this works flawlessly.

I would like to avoid using system() calls but I also have no clue why rename() would fail in this scenario.

I suppose the PHP 'rename' directly calls the system call 'rename'. It cannot move files across file systems. The 'mv' program copies the file in that case.

---

### Post by CyberJack on 2009-09-22
Have you tried a copy() and a unlink()?
It may give you a better look at what goes wrong (copy or removal of the original file).

if( copy('/home/frontend/uploadclip.xml', '/var/media/45ecfe0fb82968cd0244666d3b92ac4a2658d844') )
{
  unlink('/home/frontend/uploadclip.xml');
}

---

### Post by gencha on 2009-09-22
> **Arndt said:**
> I suppose the PHP 'rename' directly calls the system call 'rename'. It cannot move files across file systems. The 'mv' program copies the file in that case.
But the documentation at [http://us2.php.net/manual/en/function.rename.php](http://us2.php.net/manual/en/function.rename.php) states that since 4.3.3 it is able to move files across partitions.
I kinda thought that would apply here.

---

### Post by gencha on 2009-09-22
> **CyberJack said:**
> Have you tried a copy() and a unlink()?
It may give you a better look at what goes wrong (copy or removal of the original file).

if( copy('/home/frontend/uploadclip.xml', '/var/media/45ecfe0fb82968cd0244666d3b92ac4a2658d844') )
{
  unlink('/home/frontend/uploadclip.xml');
}
In fact, that works perfectly. Thanks. No idea why I didn't try that...

---

### Post by gencha on 2009-09-22
> **Arndt said:**
> I suppose the PHP 'rename' directly calls the system call 'rename'. It cannot move files across file systems. The 'mv' program copies the file in that case.
I wrote a small C application to see what rename() would give me for the same input parameters. You seem to be correct, it fails as well.
The resulting error is "Error renaming file: Invalid cross-device link". But I have yet to find out the deeper meaning of this.
Thanks though.

---

