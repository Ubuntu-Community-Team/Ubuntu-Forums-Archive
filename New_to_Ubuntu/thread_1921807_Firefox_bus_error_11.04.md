---
title: "Firefox bus error 11.04"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by alteregoash on 2012-02-07
So I've been rummaging around suggestions since last night and have yet to figure this out. The timeline goes like this:

1. I did an update roughly 2 days ago and it had an error

```
E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.
```

2. Using this thread: [http://ubuntuforums.org/showthread.php?t=1688274](http://ubuntuforums.org/showthread.php?t=1688274) I entered this:
```
sudo mkdir /var/lib/apt/lists/partial
```
and it updated fine after that.

3.However, now when I click the firefox icon it says it's opening and then doesn't. When I run it in terminal I get:
```
laptop:~$ firefox
Bus error
```

I tried a couple of suggested safe-mode start-up commands but it says the commands were not found. I've tried "killall firefox", restarting and few other suggestions but none seem to help at all.

Ideas?

(currently using chrome)

---

### Post by alteregoash on 2012-02-07
Last week I had to reinstall a file for the kernel via usb stick start up and now the software center is giving me a bus error.

Is this indicative of a hardware problem?

---

