---
title: "Can't add repository, Add Source grayed out"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by jpcstl on 2008-05-04
So I'm trying to install the medibuntu repository.  Here's what I'm doing as I understand the process:

I open up the Synaptic Package Manager
I choose Settings>Repositories>Third Party Software
I click the add button

Now this is where it gets fuzzy.  I assume I'm supposed to copy/paste the line of text for Ubuntu8.04 from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) - ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
.  BUT the Add Source button is grayed out and nothing I put in there changes that fact.  Clearly I'm doing something wrong.

---

### Post by PeterJS on 2008-05-04
If you look at the command you've got there:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
It says **sudo wget**: download with administrative privilages the file **[http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)** and (**-O**, this is why admin privileges are needed) output it to **/etc/apt/sources.list.d/medibuntu.list**.

So if you open up [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) in your browser it will have the actual list entries in it that you are trying to manually add.

---

### Post by jpcstl on 2008-05-04
So, what was I supposed to do with the code I put in my post?  Where do I put that so it does what it's supposed to?

And alternatively, you're saying I can just open the link, then copy this - deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free - into my Synaptic Package Manager?

(Yes, quite very new to this whole linux thing)

---

### Post by PeterJS on 2008-05-04
> **jpcstl said:**
> So, what was I supposed to do with the code I put in my post?  Where do I put that so it does what it's supposed to?


Commands like the one you were given need to be entered in to a terminal, which can be found at Applications > Accessories > Terminal.

> 
And alternatively, you're saying I can just open the link, then copy this - deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free - into my Synaptic Package Manager?

(Yes, quite very new to this whole linux thing)

Yep,
```

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

```
is the complete and correct repository description for medibuntu.

---

### Post by jpcstl on 2008-05-04
Excellent, thanks!  So, I used the Synaptic Package Manager and put in the text from the link you showed me.  But then I wasn't sure where/how to install the GPG key.  So I did it through terminal, and there were a couple of warnings that I (perhaps unwisely?) clicked Yes through them and it appeared to do it's thing and when the terminal command thingy (code?) was finished running, I opened back up the SPM and hit refresh and it seemed to take the key and the install of the repository!  I guess I'll know when I try to install something from it.

---

### Post by dyoung on 2008-07-18
When i go to system admin, software source and third party software , add the add source button is grayed out can anyone tell me how to correct this. Thanks

---

### Post by hyper_ch on 2008-07-18
```
cat /etc/apt/sources.list
```

---

