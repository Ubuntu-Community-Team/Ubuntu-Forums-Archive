---
title: "VC++ picture box problems - please help if you can"
date: 2006-10-30
forum: Programming Talk
---

### Post by ironfistchamp on 2006-10-30
Hey all

I know this is a long shot but with have some great programmers here who might be able to lend a hand. A friend of mine emailed me with this problem

>                                                                      
                                                                                                                                       
                                             
im using vc++ 

i have a form with 10 pictureboxes and want to be able to change the properties of the boxes by reference. in vb this is done using a control array as follow

private:
	PicBx[10] as PictureBox

Form1_Load
	PicBx[1] = PictureBox1
	PicBx[2] = PictureBox2
	etc...

Sub Make_Box_Disapear(int BxNum)
	PicBx[BxNum].Visible = false;


i want to be able to reference the pictureboxes in a simialr way so i can call on any one of the 10 to change the picture etc from a single procedure. 

I believe he is using VC++.NET. I know this isn't even Linux related but it does say any language can be posted about.

Some help on this would be brilliant. Thanks very much

Ironfistchamp

---

### Post by DavidBell on 2006-10-30
Dunno about .net but in unmanged VC it would be something like (not tested) ...

```

CStatic mPB[10];

for (long i = 0; i <10; i++)
    mPB[i].Create(NULL, WS_CHILD|WS_VISIBLE|SS_BITMAP, &myWindowRect, mHWnd);
    // skip WS_VISIBLE if you want to start invisible

mPB[0].ShowWindow(SW_HIDE);
mPB[0].ShowWindow(SW_SHOW);

// etc

// You have to bitblt to do the images 
// and handle WM_PAINT message if you want the pictures to be persistent


```

The guys on microsoft.public.vc.language newsgroup are really helpfull and _very_ knowlegable.

HTH

DB

---

### Post by ironfistchamp on 2006-10-31
Thanks very much for the response. I shall pass the information on an post back to let you know if it was what he needed. If not we shall check out that newsgroup. Thanks again

Ironfistchamp

---

### Post by DavidBell on 2006-10-31
BTW that code assumes you are using either MFC or WTL. If you want raw Win32 it's basically the same but you use an array of HWND and platform functions CreateWindow & ShowWindow. DB

---

