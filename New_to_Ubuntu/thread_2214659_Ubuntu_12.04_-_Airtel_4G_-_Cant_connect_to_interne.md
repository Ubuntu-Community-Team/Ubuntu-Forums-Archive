---
title: "Ubuntu 12.04 - Airtel 4G - Cant connect to internet"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by shumonsaha2 on 2014-04-02
My Ubuntu version is 12.04. I am using a ZTE MF825A dongle on Airtel 4G in India.
I have tried to connect using Network connections by going to mobile broadband and creating a new connection. Airtel is showing and a connection was easily created.
However, once I double click on Airtel to connect, it shows a message " Modem network disconnected - you are now offline"

Please help. I already checked some posts on similar lines but the same are very complicated for a beginner like me. Would request patience and a step by step way to solve this.

thank you

Suman Saha

---

### Post by shumonsaha2 on 2014-04-03
Hi. Please reply with some help steps.thanks.Suman

---

### Post by shumonsaha2 on 2014-04-04
OK. since no help received on this and no satisfactory guide found on net, it seems its bye bye ubuntu :-(

---

### Post by gopukrishnan on 2014-04-05
Hello Suman,

Don't give up. I also had a similar issue while configuring my MTS device using the GUI. So I have manually configured it using wvdial. Check the link how I configured it for MTS. You can change the corresponding fields for your device and give a try.
[http://gopukrish.wordpress.com/2014/04/05/configure-mts-mblaze-in-ubuntu/](http://gopukrish.wordpress.com/2014/04/05/configure-mts-mblaze-in-ubuntu/)

---

### Post by shumonsaha2 on 2014-04-05
not giving up. even now trying. but nothing seems to be working and its slightly frustrating. thanks for the reply.

---

### Post by shumonsaha2 on 2014-04-05
I have done the following
sudo apt-get installwvdial
sudo wvdial.conf /etc/wvdial.conf
sudo nano /etc/wvdial.conf

Now I am being asked to put phone number, password and login name.

Where do I get this?

---

### Post by gopukrishnan on 2014-04-06
Actually you should check that with your provider. One easy way is to configure it in a windows machine using the software coming with the datacard and you would be able to see those in the software GUI settings.

---

### Post by cruelwill on 2014-07-14
[http://askubuntu.com/questions/353478/how-to-use-airtel-4g-lte-dongle-with-ubuntu](http://askubuntu.com/questions/353478/how-to-use-airtel-4g-lte-dongle-with-ubuntu)   Find solution here.

---

