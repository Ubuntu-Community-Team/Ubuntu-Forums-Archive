---
title: "How can I transfer mp3 files to a Creative Zen player?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-07-13
I know this is a really dumb question but the first time I hooked my Creative Zen MP3 player up to my computer Rythmbox popped up showing all my songs on it.  When I put a cd in the computer and I clicked on Copy to Library it started the ripping process but I don't see an option to put those files onto the MP3 player.  
What am I missing?

---

### Post by anjilslaire on 2008-07-13
Check my blog. I've got this set up perfectly for my wife's Creative Zen V Plus. The secret is libmtpfs:

[http://anjilslaire.wordpress.com/2008/05/16/creative-zen-v-plus-on-kubuntu/]("http://anjilslaire.wordpress.com/2008/05/16/creative-zen-v-plus-on-kubuntu/")

---

### Post by Inxsible on 2008-07-13
you can mount it as a disk drive instead and just copy paste....this sometimes makes playing those songs impossiblt however..

You can also use Amarok or Rhythmbox or any muxic player that has mp3 player capability to transfer songs.

You may have to connect the device to a windows machine and do the "safely remove..." stuff in case you cannot transfer currently

---

### Post by curiousnoob on 2008-07-13
I should have been more specific.  This is actually a setup for my parents and due to a number of issues only rhythmbox can be used.  
Is there a guide anywhere on how to use rhythmbox with non ipod mp3 players?  
Am I maybe missing something real simple?

---

### Post by anjilslaire on 2008-07-13
The process is the same as I've described. It is applicable for Rhythmbox as well as AmaroK. The libmtpfs, libmtp7, etc are what is needed for proper communication. The frontend (Rhythm/Amarok, etc) don't matter. They both use the lib files to connect properly.

Install the files and then use Rhythmbox instead of AmaroK.

---

