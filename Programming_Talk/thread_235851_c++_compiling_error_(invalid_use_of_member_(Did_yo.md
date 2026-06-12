---
title: "c++ compiling error (invalid use of member (Did you forget the &amp;))"
date: 2006-08-13
forum: Programming Talk
---

### Post by Alain21 on 2006-08-13
I have something that compile perfectly under windows compiler, but cant seem to compile under G++. 

I want to pass a Pt to Function to a mapping function to add a map to the mouseClick event bla bla bla. The compiling error is on those 2 lines 

AddMap(CEntity::mapMouseClick, "BtIntroChooseLevelLeft", (TCallback)OnBtClickLeft);
AddMap(CEntity::mapMouseClick, "BtIntroChooseLevelRight", (TCallback)OnBtClickRight);

TCallback is define as : 
typedef void (CObj::*TCallback)(CEntity*);


BtClickRight and BtClickLeft are member function of "this" and "this" is an class derived from CObj. 

I cant seem to understand why this work on vc6.0 compiler and not g++ ?? different std??

---

### Post by Alain21 on 2006-08-14
Ok ... I found my error ... its differents std obviously ... 

(TCallback)&CCtxIntro::OnBtClickLeft

That seem to work

Thank you anyway for the 17 people that at least look at the post ;) so if you asked yourself how to fix this ... now  you have your answer :)

Alain

---

### Post by thumper on 2006-08-15
Your problem stemed from VC6 not being (even remotely) standards complient.

---

