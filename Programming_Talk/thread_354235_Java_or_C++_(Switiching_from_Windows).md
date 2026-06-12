---
title: "Java or C++ (Switiching from Windows)"
date: 2007-02-05
forum: Programming Talk
---

### Post by altonbr on 2007-02-05
My old roomate has created a program in BASIC that controls some sort of light in his room, running off an old Windows box he has sitting around.

He want to run these programs through a web interface. Since I'm a web developer, I offered to help him run this site.

I figured it would be easiest, though, for everyone, to install a base version of a Dapper LAMP server for greater interopitability. He's up for the idea, and since it's a simple program (parallel port hacking), he said he can ask some classmates to help him convert it to C++ or Java.

So since I'm not familiar with programming in Linux (although I'm aware of what C++ and Java are), I'm wondering what everyone would recommend he use?

He will be running applications through the terminal, ran by PHP, like this:

```
<?php

$turn_on = `./programs/turn_on_lamp`
print ($turn_on);

?>
```

What programming language would be the easiest for him to compile and for a server to run? Or should I be looking into JSP, which I know nothing about...

I found this small tutorial: [http://www.arachnoid.com/cpptutor/setup_unix.html](http://www.arachnoid.com/cpptutor/setup_unix.html) and it looked easy enough. All the server would have to have is g++ installed.. and that's only if he wanted to compile them on there.

---

### Post by lloyd mcclendon on 2007-02-05
i saw something on here (i think it was here) where somone wrote a little script to have a LED light up when he got an email.  if you can do that, the easiest way to start a program from a webserver is probably just what you posted in php.   [http://ubuntuforums.org/showthread.php?t=99082&highlight=parallel+port+LED](http://ubuntuforums.org/showthread.php?t=99082&highlight=parallel+port+LED) jsp is neat but if all you want to do is turn a light on it's not the right tool.

---

