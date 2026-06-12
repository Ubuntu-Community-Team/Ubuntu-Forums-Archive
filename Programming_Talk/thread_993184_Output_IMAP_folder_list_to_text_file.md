---
title: "Output IMAP folder list to text file"
date: 2008-11-25
forum: Programming Talk
---

### Post by diafygi on 2008-11-25
Hey all,

I am trying to create a text file with the folders in an IMAP account. I can connect to the IMAP server via openssl and get the list of folders via the "list" command, but I can't figure out how to export that list to a file. Any ideas?


EDIT: Here is my output, the lines of input are ". login", ". list", and ". logout"
```
~$openssl s_client -crlf -quiet -connect imap.gmail.com:993
Loading 'screen' into random state - done
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
verify error:num=20:unable to get local issuer certificate
verify return:1
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
verify error:num=27:certificate not trusted
verify return:1
depth=0 /C=US/ST=California/L=Mountain View/O=Google Inc/CN=imap.gmail.com
verify error:num=21:unable to verify the first certificate
verify return:1
* OK Gimap ready for requests
. login username@gmail.com *********
. OK username@gmail.com authenticated (Success)
. list "" "*"
* LIST (\HasNoChildren) "/" "INBOX"
* LIST (\Noselect \HasChildren) "/" "[Gmail]"
* LIST (\HasNoChildren) "/" "[Gmail]/All Mail"
* LIST (\HasNoChildren) "/" "[Gmail]/Drafts"
* LIST (\HasNoChildren) "/" "[Gmail]/Sent Mail"
* LIST (\HasNoChildren) "/" "[Gmail]/Spam"
* LIST (\HasNoChildren) "/" "[Gmail]/Starred"
* LIST (\HasNoChildren) "/" "[Gmail]/Trash"
* LIST (\HasNoChildren) "/" "forms"
* LIST (\HasNoChildren) "/" "lists"
. OK Success
. logout
* BYE LOGOUT Requested
. OK 73 good day (Success)
read:errno=0
```

---

### Post by Greyed on 2008-11-26
Let someone else do the heavy lifting?  

[php]
import imaplib, getpass

M = imaplib.IMAP4('mail.dmiyu.org') # put your server here...
M.login(getpass.getuser(), getpass.getpass())
boxes = M.list()
for box in boxes[1]:
    print box
M.logout()
[/php]

Results:
```

Password:                              
(\Noselect \HasChildren) "/" "mail"    
(\NoInferiors \UnMarked) "/" "mail/postponed"
(\NoInferiors \UnMarked) "/" "mail/Trash"    
(\NoInferiors \UnMarked) "/" "mail/outbox"   
(\Noselect \HasChildren) "/" "test"          
(\NoInferiors \UnMarked) "/" "Trash"         
(\NoInferiors \UnMarked) "/" "Sent"          
(\NoInferiors \UnMarked) "/" ".2005-outbox.cRZqHG"
(\NoInferiors \UnMarked) "/" "spam"               
(\NoInferiors \UnMarked) "/" "ham"                
(\NoInferiors \UnMarked) "/" "ubuntu-users"
(\NoInferiors \UnMarked) "/" "foo"
(\NoInferiors \UnMarked) "/" "Drafts"
(\NoInferiors \UnMarked) "/" "debian-devel"
(\NoInferiors \UnMarked) "/" "b5jms"
(\NoInferiors \UnMarked) "/" "debian-mentors"
(\NoInferiors \UnMarked) "/" "debian-kde"
(\NoInferiors \UnMarked) "/" "sylpheed-claws-users"
(\NoInferiors \UnMarked) "/" "debian-user"
(\NoInferiors \Marked) "/" "enigmail"
(\NoInferiors \Marked) "/" "exim-users"
(\NoInferiors \UnMarked) "/" "guru"
(\NoInferiors \UnMarked) "/" "jediprax"
(\NoInferiors \UnMarked) "/" "jobsearch"
(\NoInferiors \UnMarked) "/" "openrpg-dev"
(\NoInferiors \UnMarked) "/" "outbox"
(\NoInferiors \UnMarked) "/" "postponed"
(\NoInferiors \Marked) "/" "sa-unsure"
(\NoInferiors \Marked) "/" "ubuntu-user"
(\NoInferiors \UnMarked) "/" "txf"
(\NoInferiors \UnMarked) "/" "Queue"
(\Noselect \HasChildren) "/" "outbox-old"
(\NoInferiors \UnMarked) "/" "kubuntu-user"
(\NoInferiors \UnMarked) "/" "Junk"
(\NoInferiors \Marked) "/" "xen-user"
(\NoInferiors \UnMarked) "/" "jokes"
(\Noselect \HasChildren) "/" "archives"
(\NoInferiors \UnMarked) "/" "archives/2003-outbox"
(\NoInferiors \UnMarked) "/" "archives/2004-outbox"
(\NoInferiors \UnMarked) "/" "archives/2005-outbox"
(\NoInferiors \UnMarked) "/" "archives/2006-outbox"
(\NoInferiors \UnMarked) "/" "archives/2007-outbox"
(\NoInferiors \UnMarked) "/" "archives/archive"
(\NoInferiors \UnMarked) "/" "archives/jokes"
(\NoInferiors \UnMarked) "/" "INBOX"

```

Not perfect, but then I am just providing a proof of concept that one can work with.  ;)

---

### Post by diafygi on 2008-11-26
> **Greyed said:**
> Let someone else do the heavy lifting?

Ya, I was hoping for a bash script method, but I suppose I could work with python or perl.

---

### Post by Greyed on 2008-11-26
If anyone would be able to do it in Bash it would be ghostdog74. Might need to put Bash in the subject line to get his attention, however.  I tend to only get into topics which list Python or other subjects of interest (in this case IMAP) in the subject.  I imagine the problem is that you need to interact with the imap server interactively and it is that which is preventing a simple > to a text file.  I know there are methods of scripting simple dialogs (is that the name of the tool, dialog?) but at that point you're pretty much reinventing an imap library for Bash.

---

