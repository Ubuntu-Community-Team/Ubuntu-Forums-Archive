---
title: "Update problems"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by littletrixie on 2013-04-20
I am stuck on this one.  I tried to install updates through the update manager and got a "failed to download package files" message. The message says to check my internet connection but I can connect just fine.  The body of the message is:  Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-dri-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-dri-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libglapi-mesa-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libglapi-mesa-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libxatracker1-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libxatracker1-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80].  

The IP address referenced in the message is not my IP address. I'm at a complete loss here and any tips twords solving this would be greatly appreciated.

---

### Post by Gone fishing on 2013-04-20
Go to the software centre and try changing the sources (edit > software sources) to a different server then open a terminal and ```
sudo apt-get update
``` and then see if it gets stuck on the file.

---

### Post by philinux on 2013-04-20
> **littletrixie said:**
> I am stuck on this one.  I tried to install updates through the update manager and got a "failed to download package files" message. The message says to check my internet connection but I can connect just fine.  The body of the message is:  Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-dri-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-dri-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libgl1-mesa-glx-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libglapi-mesa-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libglapi-mesa-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libxatracker1-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/libxatracker1-lts-quantal_9.0.3-0ubuntu0.1~precise1_amd64.deb) 404  Not Found [IP: 91.189.92.202 80].  

The IP address referenced in the message is not my IP address. I'm at a complete loss here and any tips twords solving this would be greatly appreciated.

Top right Gear on desktop and choose System Settings then Software & Updates. Probably look in Other Software tab. Remove those 4.

They are links to deb packages that dont exist. They are not repositories.

See [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/)

---

### Post by ibjsb4 on 2013-04-20
Im not finding "libgl1-mesa-dri-lts-quantal_9.0.3-0ubuntu0.1[COLOR=#ff0000]~precise1[/COLOR]_amd64.deb" at this address. 

[http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/)

---

### Post by philinux on 2013-04-20
> **ibjsb4 said:**
> Im not finding "libgl1-mesa-dri-lts-quantal_9.0.3-0ubuntu0.1[COLOR=#ff0000]~precise1[/COLOR]_amd64.deb" at this address. 

[http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-quantal/)

Precisely. And they are not repositories but .deb packages.

E.g. sources should look like this [http://paste.ubuntu.com/5724258/](http://paste.ubuntu.com/5724258/)

---

### Post by ibjsb4 on 2013-04-20
> **philinux said:**
> Precisely.

No, precise2 :P

---

### Post by littletrixie on 2013-04-21
Done. It took a while but I got updated. Thanks for the help.

---

### Post by littletrixie on 2013-04-21
I messed around for a while, used the advice from this forum and managed to get updated. Thanks.

---

