---
title: "Escaping double quotes in sed"
date: 2014-08-03
forum: Programming Talk
---

### Post by cj13579 on 2014-08-03
I am trying to replace a line in a file with something stored in a variable using sed but am having some difficulty because both the line I want to replace and the new line contain double quotes. I think that I have found the answer to my question in [this stackoverflow thread]("http://stackoverflow.com/questions/7517632/how-do-i-escape-double-and-single-quotes-in-sed-bash") but I'll be honest, I don't understand the answer given.

I am trying to replace this:

```
<transition on="success" to="viewLoginForm" />
```

With this:

```
<transition on="success" to="remoteAuthenticate" />
```

At the moment I have the following but it isn't working:

```
_LOGIN='<transition on="success" to="remoteAuthenticate" />'
sed -e "/<transition on="success" to="viewLoginForm" \/>/i ${_LOGIN}" /tmp/login-webflow.xml
```

I know that my problem stems from the fact that I am using a variable and I can get it working hard coding it and using single quotes but I want to avoid that if possible.

I would be very grateful if someone could help me to understand the stackoverflow answer or even better, provide me an example of what I am looking to do :-)

Many thanks!

---

### Post by Vaphell on 2014-08-03
```
$ string='blabla<transition on="success" to="viewLoginForm" />xoxoxo'
$ login='<transition on="success" to="remoteAuthenticate" />'
$ echo "$string" | sed 's:<transition on="success" to="viewLoginForm" />:'"$login"':g'
blabla<transition on="success" to="remoteAuthenticate" />xoxoxo
```

---

### Post by cj13579 on 2014-08-03
Ah ha, excellent. I think that will work for me.

Thank you very much for the quick response!

---

