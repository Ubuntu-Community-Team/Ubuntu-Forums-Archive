---
title: "Promote a *.deb for Intellij IDEA to PPA"
date: 2010-04-06
forum: Packaging and Compiling Programs
---

### Post by anatolik on 2010-04-06
Hi,

I am a java developer and use Intellij IDEA on Ubuntu. Unfortunately IDEA is not a packaged as deb and every time Intellij releases new version I need to go to site/download/manually unpack the file. I would prefer that apt-get done it for me.

Is anybody is interested in adding *.deb to Ubuntu repository? If not I could try to do it. I really want to make the installation process easier.

I found 2 projects that generate *.deb package for IDEA:
[http://github.com/trygvis/intellij-idea-dpkg](http://github.com/trygvis/intellij-idea-dpkg)
[https://launchpad.net/~yannickm/+archive/intellij-idea](https://launchpad.net/~yannickm/+archive/intellij-idea)

It looks like #2 is not developed anymore. I want to build *.deb using #1 and upload it to Ubuntu PPA.

So question is: where to start? Could you provide docs/information/links to docs. The script #1 generates *.deb file as output.

---

### Post by ymenager on 2010-04-07
Been too busy to update the script... Planning to do so sometime in the future, but won't be for a little while :)

Please note you cannot distribute the intellij idea files since that is not allowed by it's license, so uploading it to a public PPA would put you in breach of the license.

That's why my .deb package will go download the tar file when installed.

Feel free to have a look at the code that is on launchpad bzr, you can easily update it to the latest version

---

