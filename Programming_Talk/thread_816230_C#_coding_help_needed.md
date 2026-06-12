---
title: "C# coding help needed"
date: 2008-06-02
forum: Programming Talk
---

### Post by RebounD11 on 2008-06-02
Hello everyone... I'm a HUGE newb in programming and I need a little help.

I would like to know if anyone can help me create a 3D-button (it has to be a cube) and it has to have a text label on every side. I repeat, it has to behave as a button.

Thanks in advance to anyone who tries to help me.

---

### Post by Lau_of_DK on 2008-06-02
> **RebounD11 said:**
> Hello everyone... I'm a HUGE newb in programming and I need a little help.

I would like to know if anyone can help me create a 3D-button (it has to be a cube) and it has to have a text label on every side. I repeat, it has to behave as a button.

Thanks in advance to anyone who tries to help me.

Can I pose a counter-questions? Why would a "HUGE newb" start off with a 3D cube that works as a button?

In C# you can render a 3D Cube with the OpenGL libs, and these support mouse-input on the form, but this is not a noob-task.

/Lau

---

### Post by RebounD11 on 2008-06-02
> **Lau_of_DK said:**
> Can I pose a counter-questions? Why would a "HUGE newb" start off with a 3D cube that works as a button?

In C# you can render a 3D Cube with the OpenGL libs, and these support mouse-input on the form, but this is not a noob-task.

/Lau

because this huge newb needs to finish a school-project which he doesn't like... 

can you be more specific on the "you can render a 3D Cube with the OpenGL libs, and these support mouse-input on the form" part?

---

### Post by kragen on 2008-06-02
Hmm, when you say "it has to behave as a button", can you be any more specific? Do you mean "If the user clicks on a side, each side has to do something different", or do you mean something else?

Also, how 3D does it have to be? Do you  need the ability to rotate it (for example with the mouse), or can it just be fixed.

If the answer is "it needs to rotate", then you need to look into 3D libraries (like opengl or directx). If you are doing this on linux then you will need to use opengl, but if your doing this on windows then you might have some more luck using directx or even XNA - In my experience there are more readable tutorials and guides for XNA and directx, but be warned - 3D programming definitely cant be considered easy.

BTW, how much of a "huge newb" are you? Do you understand the basics of object oriented programming etc...?

---

### Post by LaRoza on 2008-06-02
> **RebounD11 said:**
> because this huge newb needs to finish a school-project which he doesn't like... 

can you be more specific on the "you can render a 3D Cube with the OpenGL libs, and these support mouse-input on the form" part?

I assume you have read: [http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

This is your school assignment. You were given a tip to solving this (if you didn't know that tip, you are pretty far behind ;)). 

Sure you don't like the project, and you will probably not be the happiest on every project if you get a programming job. If we do you work for you, we will be torturing a fellow programmer in the future (your coworker).

---

### Post by Dylnuge on 2008-06-02
If you don't understand/know what OpenGL (or, as a Windows only alternative, DirectX) is, I wouldn't recommend working with 3D. Is this a self-defined task, where you decided that you need the cube, and there may be another way to do it? If so, try to think about another way to implament whatever. Otherwise, do some research here: [http://www.opengl.org/](http://www.opengl.org/) and here: [http://msdn.microsoft.com/en-us/vcsharp/default.aspx](http://msdn.microsoft.com/en-us/vcsharp/default.aspx)

Good luck!

PS: As LaRoza stated, there isn't anything more we can say or do to help. Try a google search if you are very stumped, and remember that programming is about thought.

---

### Post by RebounD11 on 2008-06-02
> **LaRoza said:**
> I assume you have read: [http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

This is your school assignment. You were given a tip to solving this (if you didn't know that tip, you are pretty far behind ;)). 

Sure you don't like the project, and you will probably not be the happiest on every project if you get a programming job. If we do you work for you, we will be torturing a fellow programmer in the future (your coworker).

It's not "homework". My school has a partnership with Microsoft, and if we want we can get a project from MS and if we complete that assignment we get bonuses in other classes. For every other stage we were provided with documentation ... for this one apparently not, the server where it was stored (our University Intranet Server) is down and has been that way for the past week. 

And I will not be "a fellow programmer" in the futuer since I am not a fan of programming (unless we are taking Asembly or VHDL - mostly VHDL).

I signed on for this project because it was easier (seemed so) than another class I had (non-optional this time) that was from outside my speciality (I won't get into my schools organizational details).

@kragen: it has to rotate but the behaviour of the cube is the same on every face and every face should have the same text on it.

---

### Post by RebounD11 on 2008-06-02
> **Dylnuge said:**
> If you don't understand/know what OpenGL (or, as a Windows only alternative, DirectX) is, I wouldn't recommend working with 3D. Is this a self-defined task, where you decided that you need the cube, and there may be another way to do it? If so, try to think about another way to implament whatever. Otherwise, do some research here: [http://www.opengl.org/](http://www.opengl.org/) and here: [http://msdn.microsoft.com/en-us/vcsharp/default.aspx](http://msdn.microsoft.com/en-us/vcsharp/default.aspx)

Good luck!

PS: As LaRoza stated, there isn't anything more we can say or do to help. Try a google search if you are very stumped, and remember that programming is about thought.

Thanks for the links... that's one of the answers I was seeking (you are better than Google :D)

---

### Post by kragen on 2008-06-02
> **RebounD11 said:**
> It has to rotate but the behaviour of the cube is the same on every face and every face should have the same text on it.

In that case, look up XNA or directx. There are plenty of tutorials out there, and drawing a simple 3D cube is probably one of the most straightforward tasks.
Once you have the cube working you can start looking into having it act as a button / displaying text on it.

Other than that I don't think there is any more advice I can give. Good luck!

---

