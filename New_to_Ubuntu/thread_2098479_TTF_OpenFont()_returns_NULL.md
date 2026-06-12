---
title: "TTF_OpenFont() returns NULL"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by Peach Smith on 2012-12-26
Hi, I used TTF_OpenFont to load a font, but it continually returns NULL, so I can't proceed with the rest of the text-rendering process, which after running the program without loading the font, I know it correct. TTF is initialized, and linked and included and everything is installed. The function simply returns a NULL value every time. Nobody on the internet seems to know what's going on. The few people I've seen to have this problem have solved it before anyone can post a meaningful answer. What are they doing that I'm not?

---

### Post by LouisWust on 2012-12-26
Peach Smith, would you mind posting the code which calls TTF_OpenFont?

> Nobody on the internet seems to know what's going on.Truer words have never been spoken.

---

### Post by Peach Smith on 2012-12-28
Here's the code:
    TTF_Init();

    TTF_Font *font = TTF_OpenFont("FreeSerif.ttf",24);

    if(!font)printf("Well darn, \n%s",TTF_GetError());exit(1);

    SDL_Color colour = {255,255,255};

    SDL_Surface *text=TTF_RenderText_Solid(font,"message",colour);

The TTF_GetError() tells me it couldn't load the font, but if I type in the full file path, it tells me it couldn't open the file. If I take out the if statement, the NULL font gets passed to the TTF_RenderText_Solid() function, and I get a segfault.

---

### Post by LouisWust on 2012-12-28
Have you checked the permissions on FreeSerif.ttf?

If it is not a permissions problem, post the full error message that you get when you run the code as-is, and also post the full error message that you get after you change the code to use the full pathname of FreeSerif.ttf.

If you do that, we can use the SDL source code to find out where the error is originating.

---

### Post by Peach Smith on 2012-12-28
It says the owner is root, and the access is read and write, but it also says I'm not the owner so I can't change the permissions. That particularly bugs me, as I own my computer and my account should be the one in charge. :(

---

### Post by LouisWust on 2012-12-28
> I own my computer and my account should be the one in charge.Most of the files on your Ubuntu computer are owned by the **root** user rather than your normal user account. This separation of privileges prevents you from accidentally overwriting important system files. You can use the **sudo **command to gain temporary administrative privileges. See the following article for more details:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For this situation, you won't need **sudo**. It sounds like the privileges on the font file are fine as they are.

> The TTF_GetError() tells me it couldn't load the font, but if I type in  the full file path, it tells me it couldn't open the file.Try posting the full text of the error so we can track it down.

---

### Post by Peach Smith on 2012-12-31
Well, it seems when I downloaded a font file and had owner permission, it allowed me to load the font and the program ran perfectly. I guess the permission was the problem. Thanks for your help. I would never have thought to check that.

---

