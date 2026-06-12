---
title: "remote management issue"
date: 2020-06-30
forum: New to Ubuntu
---

### Post by garyi on 2020-06-30
hi.

I have installed latest stable of ubuntu on a little nuc style pc. runs ok but I want to use it headless. I turned on sharing for vnc from the GUI. I cannot get any clients to connect they all say security is out of date or something similar or that the party did not correctly respond.

Never mind I thought i will install xrdp, appears to connect but screen is black!

is there anyway for me to get this going?

---

### Post by TheFu on 2020-07-01
After you connect to the X/Server, did you run a WM?

---

### Post by ActionParsnip on 2020-07-01
If you install lxde you can put the below in ~/.vnc/xconfig
```

#!/bin/bash
xrdb $HOME/.Xresources
startlxde &

```

You will need to run:
```

chmod +x ~/.vnc/xconfig

```

But a better question is; what are you connecting to the remote server to achieve? Why do you need VNC? What are you planning to do when you get connected?

There is probably a sleeker solution to what you are trying to do.

---

### Post by TheFu on 2020-07-01
> **ActionParsnip said:**
>  There is probably a sleeker solution to what you are trying to do.

+1
VNC is one of the worst solutions compared to the others that "just work", are more secure, and faster.

The only reason I’d use VNC was if the client was Android or iOS.  That's pretty much it. Real computers have better options and if the client is on the same LAN running an X/Server I’d use the built-in X/Windows protocol via X-Forwarding that ssh already knows how to do.  Actually, that is what i use from any Unix client machine.  From Windows or when over the internet, x2go is the way to remote desktop.

---

