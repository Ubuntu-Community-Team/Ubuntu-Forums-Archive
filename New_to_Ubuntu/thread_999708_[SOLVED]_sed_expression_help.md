---
title: "[SOLVED] sed expression help"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-12-02
I need to clean up a xml file using sed, but I don't know how to create an expression for what I need.

This is section of the text I need to clean up. It is a channel list.:

```
  <channel id="DIS">
    <display-name lang="pt">Discovery Channel</display-name>
  </channel>
  <channel id="EET">
    <display-name lang="pt">E! Entertainment Television</display-name>
  </channel>
  <channel id="FLI">
    <display-name lang="pt">Fox Life</display-name>
  </channel>
  <channel id="FOX">
    <display-name lang="pt">Fox</display-name>
  </channel>
```

I need to remove some channels from it. Each channel entry has 3 lines. I know how to match the lines with id tags or channel names, but I don't know how to remove the closing tag line </channel> without removing it from the channels I want to keep. So what I think could solve this is an expression that will delete the line with the matching id and then 2 more lines after it, regardless of their content. Is this possible?

I'm currently using expressions based on line numbers, but this is not the best solution, because if the TV provider adds more channels to the list, my filter could mess with the entire file.

---

### Post by lovinglinux on 2008-12-02
Nevermind. I figured it out.

```
-e '/id=\"EET\"/,+2d'
```

---

