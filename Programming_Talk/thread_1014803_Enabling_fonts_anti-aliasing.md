---
title: "Enabling fonts anti-aliasing"
date: 2008-12-18
forum: Programming Talk
---

### Post by evcosta on 2008-12-18
I am using Ubuntu Feisty as the foundation of an embedded project with icewm-lite as the window manager. I am running a java application and the fonts are ugly as they are not using anti-aliasing. I have installed xfce window manager and the anti-aliasing works fine. After some experimentation I found that if I can get anti-aliasing working if I start xfce4-mcs-manager under icewm. After I start my java application I may kill the manager afterwards and the fonts are rendered fine.
I browsed the manager's source code but I could not find where/how it configures anti-aliasing. I did several google searches without success. Any Idea of how I can enable anti-aliasing without using that manager?

Sorry if the question is too silly but Xorg's ways of doing things (who does what when) are not entirely clear to me (freetype, Xft, pango etc. etc. - who really does font aliasing?)

Thank you in advance for any hint.

---

