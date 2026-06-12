---
title: "Can't get stunnel to start"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by themediasnackgmai on 2016-02-02
im a bit stuck and need help understanding what im being told as there is nothing in the log file, i get the following error when i try and run stunnel (servermode):

Does it have something to do with the pid directory? There's nothing in that dir called stunnel.pid but I assumed it generates it when starting...

sudo /etc/init.d/stunnel4 start 

>     [....] Starting stunnel4 (via systemctl): stunnel4.serviceJob for stunnel4.service failed because the control process exited with error
> code. See "systemctl status stunnel4.service" and "journalctl -xe" for
> details. failed!
this is the conf file

; * Global options                                                              
*
;     **************************************************************************

; It is recommended to drop root privileges if stunnel is started by root
;setuid = stunnel4
;setgid = stunnel4

sslVersion = all

; PID file is created inside the chroot jail (if enabled)
pid = /var/run/stunnel.pid 

setuid = Jamie

cert = /etc/stunnel/private.pem
[jamietest]

accept = 10.0.2.15:5559
connect = 127.0.0.1:80

Debugging stuff (may be useful for troubleshooting)
foreground = yes
debug = 7 
output = /etc/stunnel/stunnel.log

; Enable support for the insecure SSLv3 protocol
;options = -NO_SSLv3

; These options provide additional security at some performance degradation
;options = SINGLE_ECDH_USE
;options = SINGLE_DH_USE

;include = /etc/stunnel/conf

---

### Post by Vladlenin5000 on 2016-02-02
Hi and welcome.

[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ssl-tunnel-using-stunnel-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ssl-tunnel-using-stunnel-on-ubuntu)

---

