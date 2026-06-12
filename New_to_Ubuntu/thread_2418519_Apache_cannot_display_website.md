---
title: "Apache cannot display website"
date: 2019-05-07
forum: New to Ubuntu
---

### Post by dharmil007 on 2019-05-07
Hello,

I am hosting a apache webserver on AWS EC2 using Ubuntu Server 18.04. I installed apache2 on the system.

I cannot even see the default configuration page of Apache. Whenever I enter the IP address / domain name in the URL, i Get the following error: 

```

Cannot GET /
```

The title of the page is : >  Error .

I even created a new Virtual hosts file and disabled the default, but still the same issue. I do not know what is wrong, can sombody please give suggestions?

Thanks

---

### Post by drvshrm on 2019-05-07
Did you checked for file/folder permissions...try using: 777 or 775 :

```
sudo chmod -R 777 /var/www/html/
```

---

### Post by SeijiSensei on 2019-05-07
Start with looking at the logs in /var/log/apache2.  Logs are your friend when troubleshooting.

---

### Post by TheFu on 2019-05-07
Aren't ec2 servers closed off from the internet by default. Doesn't some external setting need to be changed to allow any non-ssh access to the system?  I think this is an ec2 issue, not Ubuntu/Apache.
[https://aws.amazon.com/premiumsupport/knowledge-center/connect-http-https-ec2/](https://aws.amazon.com/premiumsupport/knowledge-center/connect-http-https-ec2/)

---

