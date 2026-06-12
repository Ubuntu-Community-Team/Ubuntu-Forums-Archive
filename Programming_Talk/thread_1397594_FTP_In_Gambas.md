---
title: "FTP In Gambas"
date: 2010-02-03
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-02-03
What's Up?

OK, So I've been trying to upload a simple file using SHELL and the ftp command.
```
SHELL "ftp -n open ftp.ftp.com user username@ftp.com passwords put file.txt close bye"
```

But it doesn't do anything, In System monitor under Waiting channel, It say's pipe wait.

Probably some easy to fix, But I'm still dumb enough not to know.

Thanks Bye!

---

### Post by Chamillionaire2 on 2010-02-05
Bumpers! Come on you know you wanna help me, Don't shy!

---

### Post by kalaharix on 2010-02-06
Hi

I can see what you are trying to do but the simple fact is that if the command within the shell statement does not work from the terminal command line (and yours doesn't!), then it won't work from Gambas.

You should be able to redirect input to the ftp program from a text file but I have not had much luck. I downloaded ncftpput (one of a suite of ncftp programs) which I think is better suited to command line usage. It allowed the following:

SHELL "/home/fred/ncftp-3.2.3/bin/ncftpput -u fred -p dog ftp.drivehq.com /PublicFolder /home/charles/testFTP.txt"

You can also do ftp natively from Gambas although the above is less verbose.

rgds

---

### Post by Chamillionaire2 on 2010-02-06
> **kalaharix said:**
> Hi

I can see what you are trying to do but the simple fact is that if the command within the shell statement does not work from the terminal command line (and yours doesn't!), then it won't work from Gambas.

You should be able to redirect input to the ftp program from a text file but I have not had much luck. I downloaded ncftpput (one of a suite of ncftp programs) which I think is better suited to command line usage. It allowed the following:

SHELL "/home/fred/ncftp-3.2.3/bin/ncftpput -u fred -p dog ftp.drivehq.com /PublicFolder /home/charles/testFTP.txt"

You can also do ftp natively from Gambas although the above is less verbose.

rgds

Thanks for replying, But what's the syntax for doing it the gambas way?

---

### Post by kalaharix on 2010-02-07
The bare bones are as follows:

> ' Gambas class file
PRIVATE theFTPClient AS NEW FtpClient

PUBLIC SUB Button1_Click()

  theFTPClient.URL = "ftp.drivehq.com/My Documents/FileToSave.txt"
  theFTPClient.User = "fred"
  theFTPClient.Password = "dog"
  
  theFTPClient.Put("/home/fred/FileToGo.txt")
END

Ideally you would do a bit more e.g. monitor theFTPClient.status to check completion.

Make sure you click on networking components when you create the project (or click on gb.net and gb.net.curl in project,properties,components)

rgds

---

### Post by keithclark on 2010-03-25
> **kalaharix said:**
> The bare bones are as follows:



Ideally you would do a bit more e.g. monitor theFTPClient.status to check completion.

Make sure you click on networking components when you create the project (or click on gb.net and gb.net.curl in project,properties,components)

rgds

When I tried this solution, I get Null Object and it stops the program at theFTPClient.URL = $URLname

---

### Post by kalaharix on 2010-03-26
Hi

Without your code it is a bit difficult to help. Gambas does have well developed debugging tools though.

You are getting an error window regarding the null object. Clear that and the program is still running though paused at the offending line.

Hover the mouse over $URLname in your code and a balloon will pop up with the current value. Alternatively type '? $URLname' in the terminal window at the bottom of the IDE. I suspect the answer will not be what you want.

rgds

---

