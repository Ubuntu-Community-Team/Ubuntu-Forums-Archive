---
title: "chmod a file"
date: 2015-01-21
forum: New to Ubuntu
---

### Post by Bubbelgum on 2015-01-21
Hello =) 


I need to add something to sources.list but iam not alowd to save, and i cant chmod 666 sources.list operation not allowed. how do i do to get it done? 

want to add 
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

so i can use spotify whit out wine

---

### Post by Rob Sayer on 2015-01-21
I seriously doubt you want to use chmod here ... and that's not something noobs should play with lightly.  BTW I think you'd need to use sudo there because that's owned by root, but that's irrelevant anyway.

I suspect this is where you got this info you're misinterpreting somewhat:

[https://www.spotify.com/ca-en/download/previews/](https://www.spotify.com/ca-en/download/previews/)

Actually it's pretty straightforward except they assume you know how to do it.  But you need sudoers level permission to edit system files.

Try what they showed in that link but edit the file using

```
gksudo gedit /etc/apt/sources.list
```

You may need to install gksu, and if your simple text editor on your DE isn't gedit substitute that name.  Actually I always install leafpad and use that.

---

### Post by Bubbelgum on 2015-01-21
Thx =)

---

