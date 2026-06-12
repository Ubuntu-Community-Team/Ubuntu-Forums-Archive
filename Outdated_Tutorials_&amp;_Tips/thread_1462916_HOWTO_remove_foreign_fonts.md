---
title: "HOWTO remove foreign fonts"
date: 2010-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by drfox on 2010-04-26
With apologies to other cultures for wanting to post this, and thanks to the world for making English the default international computer language so that we language-challenged English speakers aren't forced to learn another tongue, here is a HOW-TO remove foreign fonts in Ubuntu:

1. Open a terminal and copy and paste the following:

> sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kacst ttf-kacst-one ttf-kannada-fonts ttf-khmeros-core ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-takao-pgothic ttf-vlgothic ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei

2. Then copy and paste: 

> aptitude search ~i| grep font

3. remove any other remaining fonts you don't want **BUT:**

**DO NOT REMOVE:**
[LIST]
[*]Any xfonts or xfont utilities
[*]x-tccidfont-conf
[*]ttf-opensymbol
[*]ttf-dejavu
[*]anything that starts with lib
[*]fontconfig
[*]defoma
[*]anything that starts with console
[*]gsfonts
[/LIST]

Hope you find this useful

Larry

"*You have your way. I have my way. As for the right way, the correct way, and the only way, it does not exist*." --  **Friedrich Nietzsche**

---

