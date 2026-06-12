---
title: "How do I install Skype on Ubuntu 14.04?"
date: 2014-10-18
forum: New to Ubuntu
---

### Post by ozanji345 on 2014-10-18
Everytime I run this command:
***sudo sh -c ‘echo “deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) ******trusty partner” >> ***[I][B]/etc/apt/sources.list.d/canonical_partner.list’
[/B][/I]I get permission denied. How do I fix this?

---

### Post by Frogs Hair on 2014-10-18
Have you tried to open software & updates and enable the partners repository under the other software tab ?

---

### Post by ozanji345 on 2014-10-18
Yes I have. I still get permission denied. This is what it is telling me:

sudo sh -c &#8216;echo &#8220;deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner&#8221; >> /etc/apt/sources.list.d/canonical_partner.list&#8217;
bash: /etc/apt/sources.list.d/canonical_partner.list&#8217;: Permission denied

---

### Post by matt_symes on 2014-10-18
Hi

> **ozanji345 said:**
> Yes I have. I still get permission denied. This is what it is telling me:

sudo sh -c &#8216;echo &#8220;deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner&#8221; >> /etc/apt/sources.list.d/canonical_partner.list&#8217;
bash: /etc/apt/sources.list.d/canonical_partner.list&#8217;: Permission denied

Try this instead.

```
echo "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner" | sudo tee -a /etc/apt/sources.list.d/canonical_partner.list
```

You had some unusual characters (&#8221; != " and ` != ') in the above command you were trying to run, so copy and paste my command into the terminal.

**EDIT:**

Can you post the results fo this command into your next post as well please.

```
cat /etc/apt/sources.list.d/canonical_partner.list
```

Did you copy and paste the original command from another web page ?

Kind regards

---

### Post by Frogs Hair on 2014-10-18
Try the following and attempt to add the repository again. I assume you have permission install updates.   ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ozanji345 on 2014-10-18
Thanks!!

---

### Post by matt_symes on 2014-10-18
Hi

> **ozanji345 said:**
> Thanks!!

If you followed my post can you checkout the **EDIT:** i posted in my last post and follow that as i want to check the sources file.

If you didn't then i'm just glad it's fixed.

Kind regards

---

