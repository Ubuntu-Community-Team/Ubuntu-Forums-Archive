---
title: "x2go server"
date: 2023-05-28
forum: New to Ubuntu
---

### Post by serra-ubu on 2023-05-28
Hello, I have recently started using Ubuntu to operate my Raspberry pi 4. I need to have remote access to it and I read here in the forums that a much better option to a VNC is to use x2go.
I went through all the documentation available in their site and I managed to install the x2go server side on the Rpi and the x2go client side on the Windows PC, both running in a LAN.
Now I am stuck because when I connect the client, I only get a black screen. I am not sure how to proceed to activate correctly the Desktop Environment, although I did install XFCE on the server side.
Any help would be really appreciated!

PD. Here is the info I get from the client console:

Info: Proxy running in client mode with pid '14128'.
Session: Starting session at 'Sun May 28 14:55:07 2023'.
Info: Connecting to remote host 'localhost:34437'.
Info: Connection to remote proxy 'localhost:34437' established.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Warning: Failed to read data from the X auth command.
Warning: Generated a fake cookie for X authentication.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display 'localhost:0'.
Session: Session started at 'Sun May 28 14:55:07 2023'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.

---

### Post by ActionParsnip on 2023-05-28
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do with the pi

---

### Post by serra-ubu on 2023-05-28
I want to run machine learning iterations on python. I know it would be much better just to run the scripts in the console, but I wanted to install an IDE to inspect the status of the iterations, since I am going to implement an infinite "while True" loop.

---

### Post by ActionParsnip on 2023-05-29
What OS is the client system?

---

### Post by serra-ubu on 2023-05-30
It is Windows 10...

---

### Post by ActionParsnip on 2023-05-31
[https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-remote-desktop-with-x2go-on-ubuntu-20-04)

Does that help?

---

### Post by serra-ubu on 2023-06-02
It did help! Thanks a lot!

---

