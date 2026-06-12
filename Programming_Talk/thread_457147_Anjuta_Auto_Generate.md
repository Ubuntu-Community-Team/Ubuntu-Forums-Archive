---
title: "Anjuta Auto Generate"
date: 2007-05-28
forum: Programming Talk
---

### Post by RichC on 2007-05-28
When I try to run 'Auto generate' in Anjuta, I get the following error message:
   No package 'libgnomeui-2.0' found

I can only find 'libgnomeui-0' in Synaptic. Thinking it might help, I tried to install 'libgnomeui-dev', but then I get the following error messages:
  libgnomeui-dev:
     Depends: libgnomeui-0 (=2.14.1-0ubuntu2) but 2.14.1-0ubuntu3 is to be installed
     Depends: libgnome2-dev but it is not going to be installed
     Depends: libbonoboui2-dev but it is not going to be installed
     Depends: libgnomevfs2-dev but it is not going to be installed

The first 'Depends' error looks like it is looking for an older version of the package that is installed. When i try to install some of the other 'Depends' error packages, I just keep getting more dependency errors.

I'm running Dapper. Can anyone help with this?
Thanks,
Rich

---

