---
title: "How to fix build yocto error ?"
date: 2022-07-09
forum: Packaging and Compiling Programs
---

### Post by mm11751 on 2022-07-09
I built a Embedded Android automotive10 using yocto , it show error:
```
Your configuration files at build-x9h-plus_ref_cluster have not been touched.BSPDIR=
BUILD_DIR=.
meta-semidrive directory found
NOTE: Your conf/bblayers.conf has been automatically updated.
ERROR:  OE-core's config sanity checker detected a potential misconfiguration.
    Either fix the cause of this error or at your own risk disable the checker (see sanity.conf).
    Following is the list of potential problems / advisories:


    Fetcher failure for URL: 'https://www.example.com/'. URL https://www.example.com/ doesn't work.
    Please ensure your host's network is configured correctly,
    or set BB_NO_NETWORK = "1" to disable network access if
    all required sources are on local disk.




Summary: There was 1 ERROR message shown, returning a non-zero exit code.
ERROR:  OE-core's config sanity checker detected a potential misconfiguration.
    Either fix the cause of this error or at your own risk disable the checker (see sanity.conf).
    Following is the list of potential problems / advisories:


    Fetcher failure for URL: 'https://www.example.com/'. URL https://www.example.com/ doesn't work.
    Please ensure your host's network is configured correctly,
    or set BB_NO_NETWORK = "1" to disable network access if
    all required sources are on local disk.




Summary: There was 1 ERROR message shown, returning a non-zero exit code.
cp: cannot stat '/buildsystem-x9-ptg3.8/yocto/build-x9h-plus_ref_cluster/tmp/deploy/images/x9h-plus_ref_cluster/Image': No such file or directory
```

When I add [COLOR=#271B08][FONT=&quot]set BB_NO_NETWORK = "1" in[/FONT][/COLOR] ./yocto/poky/meta/conf/sanity.conf , it was also error, someone can tell me how to fix it?

---

### Post by mm11751 on 2022-07-10
if someone can help me?

---

### Post by TheFu on 2022-07-11
Which version of Ubuntu is this?
I suspect this belongs in the "Other OS" subforum.

I've worked in embedded software development, but wouldn't ask questions related to that in a mainstream desktop/server forum, since it is extremely unlikely that anyone there would be able to help for something so extremely specialized.  I'm just guessing, but would bet the yocto project forums would be a much better place to ask, if they exist.

---

### Post by mm11751 on 2022-07-11
> **TheFu said:**
> Which version of Ubuntu is this?
I suspect this belongs in the "Other OS" subforum.

I've worked in embedded software development, but wouldn't ask questions related to that in a mainstream desktop/server forum, since it is extremely unlikely that anyone there would be able to help for something so extremely specialized.  I'm just guessing, but would bet the yocto project forums would be a much better place to ask, if they exist.


My OS is ubuntu16.04, thanks for you advice, I will find other yocto forums to ask.

---

### Post by TheFu on 2022-07-12
> **mm11751 said:**
> My OS is ubuntu16.04, thanks for you advice, I will find other yocto forums to ask.

Standard support for 16.04 ended in April 2021. It is passed time to move to a supported release.  If you have an ESM contract, I'd read what it says about support. Bet it is just to provide security patches, but not anything for new development.  If starting a new project today, 20.04 should be used if the tools needed aren't available on 22.04 yet.  Some of the programs I use constantly only get support from the latest LTS (22.04) about a year after it is released. 20.04 support should be available by any non-dead project. It's been over 2 yrs.

---

