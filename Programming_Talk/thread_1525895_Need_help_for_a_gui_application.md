---
title: "Need help for a gui application"
date: 2010-07-07
forum: Programming Talk
---

### Post by jonian_g on 2010-07-07
Hi, I have created a new icon theme for ubuntu called Candy and I proposed it for Maverick.

The icons are developed using the one canvas work-flow (all icon sizes in one .svg file). Then, I use two scripts, one to export the icons (python) and put them in the appropriate folders and one to create the needed symlinks (bash).

If anyone is interested in creating a graphical application which can customize the colors of the icon set and use the scripts to generate the icon theme, I would be grateful.

Candy Icon Theme Launchpad page: [https://launchpad.net/candyicons](https://launchpad.net/candyicons)

Thanks in advance.

---

### Post by jonian_g on 2010-07-10
It looks like no one in these forums can help!

Do you guys know where else can I ask for help and find someone to help me?

---

### Post by phrostbyte on 2010-07-10
Writing a GUI app is easy, but the thing you want it to accomplish is a very non-trivial algorithm. You can take the SVG and marshal it into into a generic DOM object easily enough (SVG is XML). Then you query the properties of the various XML elements (eg: the "style" property). But you wouldn't be easily discover the structure of the image from the XML elements. It would just look like a series of style properties, and changing the color on those well not turn out pretty.

---

