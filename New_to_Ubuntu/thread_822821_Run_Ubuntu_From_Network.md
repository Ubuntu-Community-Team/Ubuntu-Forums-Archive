---
title: "Run Ubuntu From Network"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by mde123 on 2008-06-08
Here is what i hope you guys can help me do. I want to be able to install ubuntu on my server, and have my computers run ubuntu from network. I saw many tutorials on how to install it on a server, and be able to intall it from a server withoughht CD.

That is not what i want. I want to be able to have at least 10 computers or less be able to run ubuntu, withough installing it on there hard drives locally

---

### Post by tgrimley on 2008-06-08
What you're looking for is a way to boot PXE images of live cd's over the network.  Generally speaking this will involve setting up a PXE server and the bios in each computer to boot PXE.  PXE may go by different names, but might get you started.

---

