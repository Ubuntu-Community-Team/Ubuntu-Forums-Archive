---
title: "should I be using curl, if so how ?"
date: 2014-02-17
forum: Programming Talk
---

### Post by IAMTubby on 2014-02-17
Hello,
 I have to POST some data. I tried opening the URL in a browser by running the following command. Though it works, I would like a better method. Please find the link I'm using to POST data below.
```
chromium-browser http://54.213.213.32:8080/gprmc/Data?acct=test01&dev=test01&gprmc=$GPRMC,192417,A,2619.001183,N,05013.21068,E,0000,000.0,170214,,*7
```

After some googling, I found out about curl. But I'm not sure how to use it to POST data. I tried the following, but didn't work.
```
curl --data "acct=test01&dev=test01&gprmc=$GPRMC,192417,A,2619.001183,N,05013.21068,E,0000,000.0,170214,,*7" http://54.213.213.32:8080/gprmc/Data?
```

Please tell me how I can POST this data.

Thanks.

---

### Post by spjackson on 2014-02-17
> **IAMTubby said:**
> Hello,
 I have to POST some data. I tried opening the URL in a browser by running the following command. Though it works, I would like a better method. Please find the link I'm using to POST data below.

First, check that you **do** need to POST, because the following is a GET. (You can see this from your access log).
> 
```
chromium-browser http://54.213.213.32:8080/gprmc/Data?acct=test01&dev=test01&gprmc=$GPRMC,192417,A,2619.001183,N,05013.21068,E,0000,000.0,170214,,*7
```

What follows the /Data? is the **query string**, not POST data. If the above works, then all you need is
```

curl 'http://54.213.213.32:8080/gprmc/Data?acct=test01&dev=test01&gprmc=$GPRMC,192417,A,2619.001183,N,05013.21068,E,0000,000.0,170214,,*7'

```

---

### Post by IAMTubby on 2014-02-17
> **spjackson said:**
> 
What follows the /Data? is the **query string**, not POST data. If the above works, then all you need is
```

curl 'http://54.213.213.32:8080/gprmc/Data?acct=test01&dev=test01&gprmc=$GPRMC,192417,A,2619.001183,N,05013.21068,E,0000,000.0,170214,,*7'

```
Thank you spjackson, that worked. But I have a few questions; before I ask you, let me read up on it and get back to you in a few hours.

---

