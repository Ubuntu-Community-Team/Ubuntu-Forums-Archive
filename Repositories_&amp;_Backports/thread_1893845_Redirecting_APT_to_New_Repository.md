---
title: "Redirecting APT to New Repository"
date: 2011-12-11
forum: Repositories &amp; Backports
---

### Post by dodle on 2011-12-11
Is it possible to redirect *apt-get* to a new repository from an old one. Say, I had a repo at [color=blue]http://myoldrepo.com/apt[/color] and now I have one at [color=blue]http://mynewrepo.com/apt[/color]. Is there a way to get all calls to myoldrepo.com redirected to mynewrepo.com?

**----- EDIT -----**

I tried making [color=blue]http://myoldrepo.com/apt[/color] into an HTML file and putting a 302 redirect in it, but *apt-get* doesn't follow it.
[php]<html>
<head>

<script type="text/javascript">
  <!--
  window.location.href='http://mynewrepo.com/apt';
  -->
</script>

</head>

<body>
  This repository has moved to http://mynewrepo.com/apt

</body>
</html>[/php]

I also tried putting the new repo location in the *Filename* field of the *Packages* file:
```
Filename: http://mynewrepo.com/apt/pool/main/m/myfile/myfile.deb
```

But then it looked for the file in [color=blue]http://myoldrepo/apthttp://mynewrepo.com/apt/pool/main/m/myfile/myfile.deb[/color].

**----- EDIT -----**

Was my question clear? I want to move my repository to a new location but leave the old URL usable for people who don't know about the move.

---

### Post by dodle on 2011-12-13
*bump*

---

### Post by rowinggolfer on 2013-04-26
Old question, I know, but still high up on google search.

The answer is that since version 0.7.21, apt does support redirects. 
I had to do this with openmolar.com/debian when I moved my site to a django design.

I doubt very much, however, that apt supports javascript, which is where I suspect your method fails.

---

