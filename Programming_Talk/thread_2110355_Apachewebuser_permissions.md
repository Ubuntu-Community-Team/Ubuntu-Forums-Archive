---
title: "Apache/webuser permissions"
date: 2013-01-30
forum: Programming Talk
---

### Post by tehcavil on 2013-01-30
I know this isn't strictly a programming problem but what permissions do I give a script so that it can be called from a php script but not read by the outside user. I am using a webhost which has a turnkey solution of having php, java, on the server etc. However, I have decided to use clojure anyway by "bootstrapping" it for lack of a better word.

For example, a php page:

<?php
exec('/opt/lampp/htdocs/printme.clj',$autput);
foreach ($autput as $item){
    echo "$item";
}
?>

And the printme.clj script:

":";exec java -cp "/opt/lampp/htdocs/cljbin/clojure-1.4.0.jar" clojure.main $0 $*
(print "hello, world<br>")

-=-=-

Anyway it works, the only problem is that I cant do the permission right. Unix permissions is one of my weak spots. 

Every combination I've tried so far which allows the script to be executed allows people using the browser to read the source code of the printme.clj script!

Obviously I don't want people to see the back end scripts of the site, how do I change this?

---

### Post by spjackson on 2013-01-30
Your problem isn't with the Unix file permissions. The account under which Apache runs has to be able to read and execute the script, or you won't be able to call it. If that account can read it, then the file can be read by anyone provided that the Apache configuration allows browsing to that location.

In a hosted environment, you probably need to do this via .htaccess. However, you may already have a cgi-bin directory for which Apache is already configured in the way you want. If so, I would put the script there.

By the way, clojure rocks :P However, don't you have a startup overhead if the webserver isn't in a JVM? (I've used clojure and php but not together and I'm just curious about that.)

---

### Post by tehcavil on 2013-01-30
> **spjackson said:**
> Your problem isn't with the Unix file permissions. The account under which Apache runs has to be able to read and execute the script, or you won't be able to call it. If that account can read it, then the file can be read by anyone provided that the Apache configuration allows browsing to that location.

In a hosted environment, you probably need to do this via .htaccess. However, you may already have a cgi-bin directory for which Apache is already configured in the way you want. If so, I would put the script there.

By the way, clojure rocks :P However, don't you have a startup overhead if the webserver isn't in a JVM? (I've used clojure and php but not together and I'm just curious about that.)

There is a slight startup penalty, but I've deemed it acceptable as a price for using clojure. 

JVM startup is about ~0.35 seconds. Clojure.jar adds another second to that.

At times like this wish clojure had some sort of compile-to-binary option so I could run it natively on the server without having to start the JVM every time. Nevertheless it isn't really that bad.

Thanks for advice on editing .htacess

---

