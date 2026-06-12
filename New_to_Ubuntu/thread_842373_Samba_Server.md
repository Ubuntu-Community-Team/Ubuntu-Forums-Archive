---
title: "Samba Server?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-06-27
Hi there,

I have the following task:

I have to back up the contents of 3 Windows PCs (Word documents, excel sheets etc) on a regular basis.

At my disposal I have one PC which I am thinking of using as a file server.

All of the PCs have fixed IP addresses and thus any PC I use as a file server would automatically be available via the internet.

The backup process should be automatic.

My initial thought was to install Ubuntu and a Samba server on the PC I want to use as a file server and try to find a way to mirror the contents of "My Documents" from the Windows PCs to the server every time the computers are switched off. I thought of using the Microsoft tool "Synctoy" to do the actual copying.

Does anybody out there have any experience of this situation?

Is what I am trying to do realistic?

Are there any sites anywhere giving simple instructions on how to do this?

Thanks as ever for any answers.

Jim

---

### Post by superprash2003 on 2008-06-27
yes.. very much realistic.. you could either have the file server run a script to take files from the windows pcs or you could have the windows pcs giving the files to the ubuntu machine.. since its a windows-linux interface samba would be the right choice..you could use the software you mentioned.. just setup samba server and create share.. then maybe mount the share as a drive on your windows pc.. and use the software you said..
For Reference:How to setup samba server [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by jonabyte on 2008-06-27
What about just storing the documents on the samba server and backing that up to say a portable hard drive.
Might be less work than trying to sync all the pc's to the one server.

Just a thought.

---

### Post by Jim_in_Germany on 2008-06-27
Thanks for the replies 
> 
you could either have the file server run a script to take files from the windows pcs
That sounds interesting. How could one do such a thing? 
Do you know where I could look to get started?

> For Reference:How to setup samba server [http://prash-babu.blogspot.com/2008/...-in-linux.html](http://prash-babu.blogspot.com/2008/...-in-linux.html)
Great tut. Cheers. Just my level!

> What about just storing the documents on the samba server and backing that up to say a portable hard drive.
Might be less work than trying to sync all the pc's to the one server.
Also not bad, but would involve me being there too often.

---

### Post by superprash2003 on 2008-06-27
well create share of the client folder on the network.. and mount it on the server.. then use a tool called rsync to sync files and folders from the mounted folder to the local server

---

