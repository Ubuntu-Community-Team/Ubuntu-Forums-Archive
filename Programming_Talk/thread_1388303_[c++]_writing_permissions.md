---
title: "[c++] writing permissions?"
date: 2010-01-22
forum: Programming Talk
---

### Post by aeron005 on 2010-01-22
Hello world, I'm writing an SDL app that generates an animation and is supposed to save each frame to a bitmap as it runs, but I'm having trouble writing the actual file. My code is as follows:
```
//All drawing is complete
char fname[30];
sprintf(fname,"./Dump/screen%04d.bmp",n);
printf("Saving BMP: \"%s\"... ",fname);
if(SDL_SaveBMP(screen,fname)==0)
	printf("Success!\n");
else
	printf("Failure: %s\n",SDL_GetError());
n++;
	if(n>240)
	done=true;
```However, upon running it yields:```
Saving BMP: "./Dump/screen0000.bmp"... Failure: Couldn't open ./Dump/screen0000.bmp
```

I believe its related to permissions in ubuntu, but I'm not quite sure (running it with sudo didn't change anything)... I also tried creating the file with fopen(fname,"w") just to test, but that returns null. Any reason I wouldn't be able to write the file? It's running from my home directory, and even sudo fails. :S

---

### Post by Axos on 2010-01-23
This may be a stupid question but does the directory "Dump" exist?

---

### Post by OgreProgrammer on 2010-01-23
> **Axos said:**
> This may be a stupid question but does the directory "Dump" exist?

And check the capitalization on it too.

---

### Post by d3v1150m471c on 2010-01-23
Did you give the script authority to run as a program?

```

chmod +x path/to/script

```

---

### Post by aeron005 on 2010-01-23
> **Axos said:**
> This may be a stupid question but does the directory "Dump" exist?

Doh! Not a stupid question at all, in fact this was indeed the problem ](*,) I assumed it would automagically make the directory, but alas, this is not c# in windows ;)

Thanks for the replies!

---

