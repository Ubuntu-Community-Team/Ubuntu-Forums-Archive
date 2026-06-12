---
title: "Fixed .dmrc problem now lost access through to web files and others"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by DLLong on 2008-08-13
I ran into the $HOME/.dmrc file problem and fixed it using the following based upon the messages elsewhere in the forum - 
sudo chmod 644 home/<user>/.dmrc
sudo chown <user> /home/<user>.dmrc
sudo chmod -R 700 /home/<user>
sudo chown -R <user> /home/<user>

While it fixed the problem with the login, now I have several others and I'm sure it is due to the permissions changes above.
1.  My websites that were running on the Apache server are now no longer accessible.  I get a page not found error.
2.  When I try to access the server using Windows Explorer and through a network place I had set up, I get the messages that it "refers to a location that is unavailable." 

Can someone point me to what I need to do now?

---

### Post by unutbu on 2008-08-13
```
sudo chmod -R 700 /home/<user>
```

is quite restrictive -- it means you, the owner, get read/write/execute permission on all files in your home account, but all others get no permissions.

Perhaps try```


sudo chmod -R 755 /path/to/your/web/directory
```

This will allow others to read/execute, but not modify your web files.

You will also have to allow the parent directories to have less restrictive permissions. If your web directory is /home/<user>/www then

```

chmod 755 $HOME
chmod 755 $HOME/www/

```

---

