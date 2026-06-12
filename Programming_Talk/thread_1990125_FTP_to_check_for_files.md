---
title: "FTP to check for files"
date: 2012-05-29
forum: Programming Talk
---

### Post by CrusaderAD on 2012-05-29
Anyone familiar with FTPing into a server, having it "check" for files and returning a result? I checked the man page, but didn't see anything that might work. I need to create a quick script to check for files in an FTP directory, if there are files, email me. Any ideas?

---

### Post by codemaniac on 2012-05-29
I would prefer sshing into a server and execute a command there to check if a file exists .
something like below
```
ssh user@hostname 'ls -l'
```

or better in you case write up a local script which will do the necessary checking and execute it remotely .

```
ssh user@hostname 'bash -s' < myscript.sh
```

---

### Post by CrusaderAD on 2012-05-29
> **codemaniac said:**
> I would prefer sshing into a server and execute a command there to check if a file exists .
something like below
```
ssh user@hostname 'ls -l'
```

I thought about that, but it's a windows server I'm logging into and I don't want to go through the headache of setting up ssh and all the user / permissions.

---

### Post by codemaniac on 2012-05-29
Sorry mate , i dont have much experience dealing with Windows servers .
Hopefully other folks can help you out .best of luck .

---

### Post by CrusaderAD on 2012-05-29
> **codemaniac said:**
> Sorry mate , i dont have much experience dealing with Windows servers .

Lucky you, it's hell! :lolflag:

---

### Post by denago on 2012-05-29
Maybe use curl in a shell script?  The following line will get you a directory listing.  Just parse it for what you're looking for.

```
output = `curl ftp://username:password@example.com`
```

---

