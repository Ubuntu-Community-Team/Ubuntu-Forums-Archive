---
title: "Login screen at start-up-JavaApp"
date: 2007-03-07
forum: Programming Talk
---

### Post by derby007 on 2007-03-07
My Java application will have a LOGIN screen shown to the user on start-up, so i created my main Frame & then added an InternalFrame as the Login screen, but as i added other buttons etc to the main Frame, when i run the app the Internal Frame gets hidden or partially hidden, is there a way to make this the default screen on start-up, ie. hasFocus() so that the user must use this window at start-up?

---

### Post by Ragazzo on 2007-03-07
Are you using both AWT and Swing components (starts with J)? If you do, AWT components can overlap a Swing component when they should be below it.
[http://java.sun.com/products/jfc/tsc/articles/mixing/](http://java.sun.com/products/jfc/tsc/articles/mixing/)

You can use Dialog, or JDialog, and set it modal. Modality means that input to other (your program's) windows is blocked as long as the dialog is showing.

---

### Post by derby007 on 2007-03-07
Ah yes, the trick is to use modal. 
I'm using SWING.
Q. Have you seen the FREE DESIGN layout in Netbeans, and can it be imported into SunJavaStudioEnterpriseEdition8 ? 
Having to set everything to AbsoluteLayout etc is pain/stake/ingly sloooow.......:(

---

