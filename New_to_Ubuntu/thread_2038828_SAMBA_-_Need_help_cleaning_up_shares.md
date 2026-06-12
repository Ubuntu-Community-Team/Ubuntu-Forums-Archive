---
title: "SAMBA - Need help cleaning up shares"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by Slownis on 2012-08-07
Somehow I ended up with multiple shares set up under SAMBA for the same directory on a drive named 'Bella'.  Here is the contents of my usershare directory:

```
johnw@johnw-desktop:/var/lib/samba/usershares$ ls
backups             itunes on bella    recorded tv on bella
backups on bella    movies             tv shows on bella
bella               movies on bella    videos on bella
documents           music              windowsimagebackup
documents on bella  music on bella     windowsimagebackup on bella
downloads           pictures           zoom
downloads on bella  pictures on bella
itunes              recorded tv
```I've tried cleaning this up using the gui interface and I can remove the '* on bella' shares, but the other shares like music, backups, etc can not be removed.

Interestingly enough, the 'backups', 'documents', etc shares are owned by root while the 'backups on bella', 'documents on bella', etc shares are owned by my user id.

Can I just use the command line and sudo and rm the shares I don't want in this folder, or is there more involved?

I also tdbdump'ed the contents of share_info.tdb:

```
johnw@johnw-desktop:/var/lib/samba$ sudo tdbdump share_info.tdb
{
key(16) = "SECDESC/backups\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(24) = "SECDESC/itunes on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(27) = "SECDESC/documents on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(27) = "SECDESC/windowsimagebackup\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(20) = "SECDESC/recorded tv\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(26) = "SECDESC/pictures on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(18) = "SECDESC/downloads\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(15) = "SECDESC/videos\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(25) = "SECDESC/backups on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(29) = "SECDESC/recorded tv on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(15) = "SECDESC/movies\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(23) = "SECDESC/music on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(36) = "SECDESC/windowsimagebackup on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(26) = "SECDESC/tv shows on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(17) = "SECDESC/pictures\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(27) = "SECDESC/downloads on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(13) = "SECDESC/zoom\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(24) = "SECDESC/videos on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(13) = "INFO/version\00"
data(4) = "\02\00\00\00"
}
{
key(15) = "SECDESC/itunes\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(18) = "SECDESC/documents\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(24) = "SECDESC/movies on bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(14) = "SECDESC/music\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(17) = "SECDESC/tv shows\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
{
key(14) = "SECDESC/bella\00"
data(48) = "\01\00\04\80\00\00\00\00\00\00\00\00\00\00\00\00\14\00\00\00\02\00\1C\00\01\00\00\00\00\00\14\00\FF\01\1F\10\01\01\00\00\00\00\00\01\00\00\00\00"
}
```Do I need to modify the contents of this file also?  Or is one of those things where I can just delete the file and restart samba and all will be good?

thanks!

---

### Post by Morbius1 on 2012-08-07
It appears you created some shares with your own user name and others as gksu. Just go into the folder as root:
```
gksu nautilus /var/lib/samba/usershares
```And delete the one's you don't want.

No need to restart samba.

---

