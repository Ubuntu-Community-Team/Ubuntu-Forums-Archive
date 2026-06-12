---
title: "Pulling data through foreign javascript bot-blockers"
date: 2007-10-06
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-10-06
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

I took on a new client this week.

They needed a spider to pull data on tax liens from publically accessible databases on the internet.

This is no problem - I've written bot utilities before for similar situations. No big deal.

Except they need info from *specific* data sources, which I've begun to explore.

What wasn't explained to me prior to signing the contract was that each of these data sources has a javascript component pulling data for display in the browser.

Is there a well-documented Java method for pulling data through javascript query componentry? I've checked around on the internet and in my own Java reference materials but there's little to be said in particular on this topic matter.

I'm confident that I can get this figured out on my own, but it's going to take some time, and I'd like to get the data to these folks as soon as possible.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFHCAcxhnZ133XoNC8RArc4AJ4zeFZXvBoWLwQYECLmazPGlOslogCgqFR7
vgRKmtUvP2eNl6uL4BNtJBE=
=54Mc
-----END PGP SIGNATURE-----

---

### Post by Wybiral on 2007-10-06
It's probably specific to the Javascript interface being used. Does it look like hand written or server generated Javascript?

---

### Post by Carl Hamlin on 2007-10-06
Probably hand-generated but propogated by processes internal to the database they're using. Here's the output I recieve from OpenStream():

```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<!-- 
index.html 
Copyright (C)2001-2005 The Main Line Corporation - www.mainlinecorp.com
-->
<html lang="en">
<head>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
<meta name="copyright" content="Copyright (C)2001-2005 The Main Line Corporation">
<META NAME="robots" CONTENT="nofollow">
<META HTTP-EQUIV="Window-target" CONTENT="_top"> 
<NOSCRIPT>
<META HTTP-EQUIV="refresh" CONTENT="0;URL=/Scripts/Coverpage.dll/noscript"> 
</NOSCRIPT>
<META HTTP-EQUIV="refresh" CONTENT="0;URL=/Scripts/Coverpage.dll/index"> 
<title>ACRIS Main Options</title>
<SCRIPT language=JavaScript>
        if((top.document.referrer.length == 0) ||
                ((top.document.referrer.indexOf("nyc.gov") == -1) &&
                (top.document.referrer.indexOf("ny.us") == -1))) {
                top.document.location.href="http://www.nyc.gov/acris";
        }
               else {
          document.cookie = "JUMPPAGE=YES; PATH=/; DOMAIN=a836-acris.nyc.gov";
        }
</SCRIPT>

</head>
<body>
If your browser does not automatically advance within a few seconds, please click on <a href="/Scripts/Coverpage.dll/index">ACRIS Main Options</a>
</body>
</html>

```

What I *need* is the data the javascript pulls. Thanks for helping me.

---

