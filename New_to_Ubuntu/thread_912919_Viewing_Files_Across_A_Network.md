---
title: "Viewing Files Across A Network"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by ajaysutton on 2008-09-07
Greetings,

I'm A. Jay, and a relative newbie to Ubuntu and I've got a question I cannot find the answer to here in the Forums.  If it's been answered previously, I'll beg your forgiveness and thank you for pointing me in the right direction...

I've got a pair of Linux boxes on my network (one runs Ubuntu, and is called gx110, the other runs Xubuntu and is called smallbox).  My router is a VisionNet M202 or 205 DSL gateway, I'm doing DHCP across the network and everybody can hit the internet with no problem.

I've actually managed (with the help of a knowledgeable friend) to get Synergy installed and working the way I want it to work which I'm very pleased about, but there's one small hurdle I can't seem to overcome, I'm hoping someone here can help.

I do a little bit of HTML and all of that lives on gx110, I use Bluefish as an editor but would like to display the page I'm editing in a browser on small box so I can see the page and edit it at the same time (realizing of course that I need to refresh the browser every time I want to see a change and what not)

I stumbled across Nautilus and was actually able to even share the folder with the web sites that I want to share.  Now for the Newb part...

I don't know how to view the files that I've shared on gx110 when I'm on smallbox.  I've tried putting the IP in the browser window as I would with Windows to see if it would show me available shares or something like that.  On both boxes the user name and password that I'm logging in with are identical, so I'm not sure what I'm missing.  I'm sure it's fairly simple.

I've done a lot of Windows file sharing in the past so I'm not completely unfamiliar with the concept, I'm just not quite up to speed on Linux yet.

Thanks so much.

A. Jay

---

### Post by Pro-reason on 2008-09-07
You can share files between two Linux boxes by using Samba, NFS or SSH.  I use all three.

---

### Post by owenll on 2008-09-07
I have OpenSSH and find it very useful and easy to use:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by ajaysutton on 2008-09-07
Thanks for your very prompt reply...  I understood Samba was only for doing Windows shares from Linux boxes, but I may have misunderstood.  I ssh into Linux boxes at work frequently, but what I'd like to be able to do is display a local web page that lives on gx110 on the screen attached to smallbox, while I've got the source opened in Bluefish on gx110.  

Have I said it correctly?  I'm worried that I'm not saying it right and so people won't know what I'm trying to do.

I've actually got the folder with the web site in shared on gx110, I did that with Nautilus, what I can't seem to be able to do is view that share from smallbox.

Thanks again.

---

### Post by ajaysutton on 2008-09-07
Perhaps another way to say it is to say that if this were Windows, I'd expect to be able to browse to a network share, but on smallbox (which runs xubuntu) I can't find any options like that.

---

### Post by Pro-reason on 2008-09-07
Yes, it would be possible to do what you are describing with Samba, NFS or SSH/SFTP.  Any of them could do it.  Just look up the documentation for any of them, and follow it.

Come back if you have any problems at all.

---

### Post by ajaysutton on 2008-09-07
I think that'll help.  However, I was looking at Samba.org, and it doesn't seem all that clear to me.  Do you know of a good How To?  It doesn't seem to me like it should be as complciated as it appreared on the Samba site.

Thanks again.

---

### Post by Xiong Chiamiov on 2008-09-07
While it is true that [Samba]("http://delicious.com/xiong.chiamiov/samba") will work for sharing files *nix-to-*nix, it's designed for sharing with Windows.  Using [NFS]("http://delicious.com/xiong.chiamiov/nfs") will get you much better performance.

You can also forward GUI apps across ssh:
```

ssh -X <remote_server> /usr/kde/3.5/bin/kcontrol

```

Personally, I use [Komodo Edit]("http://www.activestate.com/Products/komodo_ide/komodo_edit.mhtml"), which allows me to edit files across an FTP (or SFTP) connection - very helpful when your server is remote, or when working on a iMac (no package management - grr!).

---

### Post by ajaysutton on 2008-09-08
Greetings all,

I wanted to share with you what finally helped me to do what I was able to do in case any other newb encounters a situation like this:

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Thanks for all your direction and prompt responses.

A. Jay

---

