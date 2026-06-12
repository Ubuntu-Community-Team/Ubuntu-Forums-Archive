---
title: "btdownloadcurses creates files which are owned by root"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Borack on 2008-11-06
Hi all!

I installed the ubuntu server 8.04 on my apple powermac g4. everything worked fine till yesterday. 

I want to use the ubuntur server for downloading torrents, start them remotely with ssh- which did already work fine. 

i have the bittornado package installed and use btdownloadcurses for the downloads. 

but since yesterday the files created after 'btdownloadcurses 'webadress-to-torrent-file' ' are owned by root. and after a short time btdownloadcurses shows status: download failed. 
then i get the error message: Couldn't allocate dir - [Errno 13] Permission denied:  path/to/file

When i check the newly created folders, then i see that they are owned by the root and i have only read access. 

i already did some downloads and there the files/folders are owned by myself . 

so i did probably something dumb in the meantime ? .. but i don't think that i did something special .. or at least i can't rember  :-)


Does anyone know what causes this problem ? 


Cheers
- Borack

---

