---
title: "Help with subversion...compatibility problem?"
date: 2007-03-15
forum: Programming Talk
---

### Post by smitjel on 2007-03-15
Maybe some of you other developers can help me out...I'm having some trouble with subversion.  When I issue the checkout command, I'm getting connection refused errors.

I have a project hosted on a box running Edgy Server, with subversion 1.3.2 (installed via apt-get).  I have another box running Fedora Core 5 with subversion 1.3.2 and I can checkout the project just fine.

I want to check out the project on a Dapper Server box, running subversion 1.3.1 (installed via apt-get).  When I issue the checkout command, I get connection refused.

Do I have a versioning problem?  Do I _have_ to have the exact same version of subversion on the client machine as the server to be able to checkout from the repository?  Thanks for ANY help!  ](*,)

```
svn checkout svn://xx.xxx.xx.x/myrepo/MyProjectName MyProjectName
svn: Can't connect to host 'xx.xxx.xx.xx': Connection refused
```

---

### Post by blanky on 2007-03-15
Honestly I have no idea, but maybe it's firewall issues on either one of the computers? Maybe you specifically allowed the Fedora one? But forgot to allow the Dapper one? Or maybe it's iptables? Try **iptables -L** and see. I don't think there should be a problem with the versions. If you would like more specific help from more knowledgeable people (*I'm just trying to help, but I'm no expert*), you should check out irc.freenode.net #svn, they can really help.

---

### Post by geirha on 2007-03-16
Do you have ssh-access? if so, you can tunnel through ssh:

```
svn checkout svn+ssh://host/myrepo...
```

then you won't need to configure a subversion-server.

---

