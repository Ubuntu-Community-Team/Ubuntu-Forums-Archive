---
title: "[SOLVED] running scripts in $PATH - permission denied"
date: 2008-10-02
forum: Programming Talk
---

### Post by r3bol on 2008-10-02
I'm following Byte of Python and trying to set up a environment where my scripts can be run from anywhere. I setup my own $PATH variable, but get a Permission denied error when trying to run my scripts. Here is how I did it and some things I tried to make it work. 
 
leke@leke-desktop:~$ PATH=$PATH:/home/leke/dev/bin
leke@leke-desktop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/leke/dev/bin
leke@leke-desktop:~$ test.py
bash: /home/leke/dev/bin/test.py: Permission denied
leke@leke-desktop:~$ sudo test.py
[sudo] password for leke: 
sudo: test.py: command not found
leke@leke-desktop:~$ chmod a+x /home/leke/dev/bin
leke@leke-desktop:~$ test.py
bash: /home/leke/dev/bin/test.py: Permission denied

What am i doing wrong here?
Thanks.

---

### Post by ad_267 on 2008-10-02
You probably haven't made the script executable. Try this:

```
chmod +x /home/leke/dev/bin/test.py
```

Edit: Just saw you tried "chmod a+x /home/leke/dev/bin". That was close but you need to make the actual files executable, you could use "chmod a+x /home/leke/dev/bin/*".

And make sure you have "#!/usr/bin/env python" as the first line of your script.

---

### Post by r3bol on 2008-10-02
> **ad_267 said:**
> You probably haven't made the script executable. Try this:

```
chmod +x /home/leke/dev/bin/test.py
```

Edit: Just saw you tried "chmod a+x /home/leke/dev/bin". That was close but you need to make the actual files executable, you could use "chmod a+x /home/leke/dev/bin/*".

And make sure you have "#!/usr/bin/env python" as the first line of your script.
Thanks, that worked and I did need to use #!/usr/bin/env python
I just googled what #!/usr/bin/env means too. Nice to know!

---

