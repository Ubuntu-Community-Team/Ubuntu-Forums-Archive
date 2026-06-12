---
title: "lftp errors"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by jus71n742 on 2008-05-17
I am trying to lftp some files from a server to my computer so I can work on them at my place on my computer. I am getting some errors and since this is the first time I have used lftp I am kinda unsure how to go about it.
I have tried the following after loging into the other server 
cp -R ~/directory I want ~/where I want it on my computer
mirror -r ~/directory I want ~/where I want it
mirror -R ~/directory ~/where I want it

the cp - R was used in the ssh shell and it wouldn't work 
the mirror -r would attempt to connect then continuously retry with longer wait times each time
the mirror -R would say that the file on the server was nonexistent 

any suggestions?

---

### Post by Monicker on 2008-05-17
From your description, it is unclear to me as to whether you actually established a connection to the ftp server.  Can you post some of the output from your connection attempts?

---

### Post by jus71n742 on 2008-05-20
lftp [email]jedwar@hydra1.cs.utk.edu[/email]:~> mirror -R ~/cs102 ~/documents/cpp/cs102
mirror: Access failed: /home/justin/cs102: No such file or directory
1 error detected


lftp [email]jedwar@hydra1.cs.utk.edu[/email]:~> mirror -r ~/cs102 ~/documents/cpp/cs102
cd `~/cs102' [Delaying before reconnect (time left)]

---

