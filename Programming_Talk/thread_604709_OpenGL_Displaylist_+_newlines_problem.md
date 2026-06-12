---
title: "OpenGL Displaylist + newlines problem"
date: 2007-11-06
forum: Programming Talk
---

### Post by paukku92 on 2007-11-06
Hello i'm trying to make a text drawing function and i have made a working version but I want to make the text to jump to a new line when a newline char is found.

```

for(int i=0;i<strlen(string);i++)
{
	if(string[i]!='\n')
	{
		glPushAttrib(GL_LIST_BIT);
		glListBase(FontList);
		glCallLists(1,GL_UNSIGNED_BYTE,(GLubyte *)string[i]);
		glPopAttrib();
	}
	else
	{
		glRasterPos2i(int(X*GUI_ScreenWidth),int(GUI_ScreenHeight-(GUI_ScreenHeight*Y))-height*Y);
	}
}

```

This throws segmentation fault. How should I call the list.

---

