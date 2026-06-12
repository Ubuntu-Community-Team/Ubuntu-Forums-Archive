---
title: "Simple C programming question"
date: 2009-08-08
forum: Programming Talk
---

### Post by Nerdriot on 2009-08-08
Hello,

So I'm just getting into creating homebrew for my PSP, and have managed to get the very basics down, even going as far as writing a simple program to load pictures (nothing major).

My question though is about a simple control I was told to add in, to keep the buttons from repeating, since the buttons require a while loop to be read (which I don't understand fully).

Here is the part I'm confused about:

```

while(1) {
sceCtrlReadBufferPositive(&pad, 1);
if (pad.Buttons != lastpad.Buttons) {
lastpad = pad
```

The "lastpad = pad" part confuses me. It prevents it from repeating, but lastpad always remains "pad" after that. Then, the if statement for the button press...

```
if (pad.Buttons & PSP_CTRL_CROSS) {
printf("Text.\n");
}
}
```

Somehow, this prevents the buttons presses from repeating rapidly while it continues with the loop, but I'm not exactly sure how. It seems like, once "lastpad = pad", it shouldn't work any more than one time period.

Can anyone explain this to me? I'm still really new to this...

---

### Post by dwhitney67 on 2009-08-08
Bear in mind that the computer, or in your case the PSP, will do exactly what you program it to do.

The code you presented is obviously syntactically correct, however from what you describe, the s/w probably failing to meet one of your requirements.

In order to assist you, it would be helpful if you provided the following:  1) your requirements, and 2) a complete listing of your callback function that handles button presses.  Also, comment your code where necessary so that it is easy to understand what you are attempting to accomplish.

P.S.  As an aide to improve the readability of C code, it is helpful that you indent 2 or more spaces (or sigh, a tab-space) when you enter a level, or block, of code that is partitioned with the {} brackets.  Adding horizontal and/or vertical white-space also helps.

IMO, the following is easier to read:
```

while(1) {
   sceCtrlReadBufferPositive(&pad, 1);

   if (pad.Buttons != lastpad.Buttons) {
      lastpad = pad
      ...
   }
   ...
}

```

---

### Post by paukku92 on 2009-08-08
Let me guess, the code is something like this:

```

while(1) {

sceCtrlReadBufferPositive(&pad, 1);
if (pad.Buttons != lastpad.Buttons) {
      lastpad = pad;
      
      if (pad.Buttons & PSP_CTRL_CROSS) {
           printf("Text.\n");
      }
}
}
```

The key is checked only if the state of buttons has changed. So if you press the cross button, it sees that the button state has changed and prints "Text.". Because now lastpad=pad it only checks next time when the buttonstate changes.

However i think that there is a small flaw in this logic. If you press down another button, the state changes and the cross button gets checked again event if it hasn't been released in between.

---

### Post by chanidu87 on 2009-08-08
> **Nerdriot said:**
> Hello,

So I'm just getting into creating homebrew for my PSP, and have managed to get the very basics down, even going as far as writing a simple program to load pictures (nothing major).

My question though is about a simple control I was told to add in, to keep the buttons from repeating, since the buttons require a while loop to be read (which I don't understand fully).

Here is the part I'm confused about:

```

while(1) {
sceCtrlReadBufferPositive(&pad, 1);
if (pad.Buttons != lastpad.Buttons) {
lastpad = pad
```The "lastpad = pad" part confuses me. It prevents it from repeating, but lastpad always remains "pad" after that. Then, the if statement for the button press...

```
if (pad.Buttons & PSP_CTRL_CROSS) {
printf("Text.\n");
}
}
```Somehow, this prevents the buttons presses from repeating rapidly while it continues with the loop, but I'm not exactly sure how. It seems like, once "lastpad = pad", it shouldn't work any more than one time period.

Can anyone explain this to me? I'm still really new to this...

Were you able to fix this C program ? Else i can help you, PM me.

---

### Post by Nerdriot on 2009-08-08
> **paukku92 said:**
> Let me guess, the code is something like this:

```

while(1) {

sceCtrlReadBufferPositive(&pad, 1);
if (pad.Buttons != lastpad.Buttons) {
      lastpad = pad;
      
      if (pad.Buttons & PSP_CTRL_CROSS) {
           printf("Text.\n");
      }
}
}
```

The key is checked only if the state of buttons has changed. So if you press the cross button, it sees that the button state has changed and prints "Text.". Because now lastpad=pad it only checks next time when the buttonstate changes.

However i think that there is a small flaw in this logic. If you press down another button, the state changes and the cross button gets checked again event if it hasn't been released in between.

Well, I'm still really new to this, so what do you think would be a better way of doing it? I mean, this *does* work, but for some reason, it doesn't seem logical to me. It seems that it's saying, "Read the buttons at pad1, and if lastpad isn't the same as pad, then now it is (which seems like it shouldn't read for button presses anymore, since sceCtrlReadBufferPositive checks "pad", not "lastpad"). Allow the action to be performed once this button is pressed, but not anymore."

I'm so confused...

It is doing what I want it to do, though. Normally, the loop runs so fast that, when you press a button once, it will repeat it several times before you've even let off the button. With that "lastpad = pad" portion in, it only prints one time per button press, which is what I was aiming for. I just can't seem to figure out WHY it works... I'm such a noob, lol.

---

### Post by Nerdriot on 2009-08-08
> **dwhitney67 said:**
> Bear in mind that the computer, or in your case the PSP, will do exactly what you program it to do.

The code you presented is obviously syntactically correct, however from what you describe, the s/w probably failing to meet one of your requirements.

In order to assist you, it would be helpful if you provided the following:  1) your requirements, and 2) a complete listing of your callback function that handles button presses.  Also, comment your code where necessary so that it is easy to understand what you are attempting to accomplish.

P.S.  As an aide to improve the readability of C code, it is helpful that you indent 2 or more spaces (or sigh, a tab-space) when you enter a level, or block, of code that is partitioned with the {} brackets.  Adding horizontal and/or vertical white-space also helps.

IMO, the following is easier to read:
```

while(1) {
   sceCtrlReadBufferPositive(&pad, 1);

   if (pad.Buttons != lastpad.Buttons) {
      lastpad = pad
      ...
   }
   ...
}

```

I'm sorry, I'm still really new, so I'm probably extremely vague when I explain stuff, lol... just bear with me ;)

Here is the full code, with callbacks:

```
#include <pspdisplay.h>
#include <pspctrl.h>
#include <pspkernel.h>
#include <pspdebug.h>
#include <pspgu.h>
#include <png.h>
#include <stdio.h>
#include "graphics.h"

#define printf pspDebugScreenPrintf
#define MAX(X, Y) ((X) > (Y) ? (X) : (Y))

PSP_MODULE_INFO("Test", 0, 1, 1);

// Exit callback

int exit_callback(int arg1, int arg2, void *common) {
	sceKernelExitGame();
	return 0;
}

int CallbackThread(SceSize args, void *argp) {
	int cbid;

	cbid = sceKernelCreateCallback("Exit Callback", exit_callback, NULL);
	sceKernelRegisterExitCallback(cbid);

	sceKernelSleepThreadCB();

	return 0;
}

int SetupCallbacks(void) {
	int thid = 0;

	thid = sceKernelCreateThread("update_thread", CallbackThread, 0x11, 0xFA0, 0, 0);
	if (thid >= 0) {
		sceKernelStartThread(thid, 0, 0);
	}

	return thid;
}

int main()
{
SceCtrlData pad, lastpad;

pspDebugScreenInit();
SetupCallbacks();

printf("Test.\n\n");
printf("Press [X] or [O]:\n");


while(1) {
sceCtrlReadBufferPositive(&pad, 1);
if (pad.Buttons != lastpad.Buttons) {
	lastpad = pad;

	if (pad.Buttons & PSP_CTRL_CROSS) {
		printf("[X] pressed.\n");
		}

        else

        if (pad.Buttons & PSP_CRTL_CIRCLE) {
                printf("[O] pressed.\n");
                }
	}
}

sceKernelSleepThread();
return 0;
}
```

Initially, without "lastpad = pad", the code loops so quickly, that once a button is pressed, an action is performed multiple times as a result. The idea was to limit the amount of actions performed to one single action. So, when I pressed [X] without that, it would do this:

```
[X] pressed.
[X] pressed.
[X] pressed.
[X] pressed.
[X] pressed.
[X] pressed.
```

Whereas now, it only prints it once, which was my aim.

My only issue is, I'm not sure HOW that prevents it from printing it so many times. Maybe I just don't have enough understand of what is going on "behind the scenes", but the "lastpad" potion just doesn't seem like it would prevent it. To me, it seems like it would only allow one button press while the loop is going, and only one action, period. Nothing more after that one press and action, forcing me to have ANOTHER loop to do something else, but that's not the case.

---

### Post by gtr32 on 2009-08-08
Does this make anymore sense to you? It's quite logical behaviour once you get a hang of it.

while(1) /* endless loop */
{
[INDENT]read current keypress;[/INDENT]
[INDENT]only if current keypress does not equal what the previous keypress was
{[/INDENT]
[INDENT][INDENT]/* keypress value has changed */[/INDENT][/INDENT]
[INDENT][INDENT]assign previous keypress the value of current keypress
print what the value of current keypress was[/INDENT][/INDENT]
[INDENT]}[/INDENT]

}

---

### Post by Nerdriot on 2009-08-08
OH! I get it now! I was looking at it all wrong...

So if I'm understanding, the key you press gets assigned as "pad", and the compared to "lastpad". If it's not the same, it continues and prints. If it does, it won't print...

So does that mean that, every time the loop starts over, "pad" becomes blank? If so, that explains my whole confusion. I was thinking that "pad" retains what the last button pressed was, regardless. But it makes sense that, every time the code cycles, it's reading for a new button press, and "erasing" the old one from "pad".

That paragraph was messy, but, am I correct in thinking that "pad" becomes "blank" as it waits for a new button?

EDIT: I figured it out, finally. Your explanation helped a ton. Thank you!

---

### Post by gtr32 on 2009-08-08
> **Nerdriot said:**
> That paragraph was messy, but, am I correct in thinking that "pad" becomes "blank" as it waits for a new button?

That code reads the current key to value pad. So if you hold down key Y, lastpad gets assigned the value Y. When you release key Y, pad gets assigned a value that represents no key press (or that sceCtrlReadBufferPositive keeps waiting for a keypress, I don't know how that function works).

Now you press key X, that code reads:

[INDENT]   /* if ( X != Y ) { */
   if (pad.Buttons != lastpad.Buttons) {
      [INDENT]/* lastpad.Buttons value becomes X */
      lastpad = pad[/INDENT][/INDENT]

You keep pressing down X:

[INDENT]   /* if (X != X ) { */
      [INDENT]/* we don't go here since X equals X */[/INDENT][/INDENT]

---

### Post by Nerdriot on 2009-08-08
> **gtr32 said:**
> That code reads the current key to value pad. So if you hold down key Y, lastpad gets assigned the value Y. When you release key Y, pad gets assigned a value that represents no key press (or that sceCtrlReadBufferPositive keeps waiting for a keypress, I don't know how that function works).

Now you press key X, that code reads:

[INDENT]   /* if ( X != Y ) { */
   if (pad.Buttons != lastpad.Buttons) {
      [INDENT]/* lastpad.Buttons value becomes X */
      lastpad = pad[/INDENT][/INDENT]

You keep pressing down X:

[INDENT]   /* if (X != X ) { */
      [INDENT]/* we don't go here since X equals X */[/INDENT][/INDENT]

That makes sense. It seems like, the reason it was looping before was because, sceCtrlReadBufferPositive(&pad, 1); was like this...

```
while(1) {
     sceCtrlReadBufferPositive(&pad, 1);
     if (pad.Buttons & PSP_CTRL_CROSS) {
          printf(Cross was pressed, woo!\n.");
         }
}
```

And if I understand that right, it was looping back so quickly that "pad" was getting assigned "cross" again before you'd even released the button, thus allowing a sort of "rapid-fire" key press.

Having this control in here definitely makes it a lot easier.

Thank you again for your help! I think I understand it more now. I knew that it worked, but I just wanted to know *why* it worked, so in the future I could do something similar if I ever had to, and understand why I had to do it.

---

### Post by gtr32 on 2009-08-08
> **Nerdriot said:**
> And if I understand that right, it was looping back so quickly that "pad" was getting assigned "cross" again before you'd even released the button, thus allowing a sort of "rapid-fire" key press.

That code reads the key as fast as it can, which brings in another issue. This is platform and case dependent but in many cases it would wise to let the loop idle a short time before starting over again. This will prevent the processor to get 100% load.

```

while(1) {
sceCtrlReadBufferPositive(&pad, 1);
if (pad.Buttons != lastpad.Buttons) {
	lastpad = pad;

	if (pad.Buttons & PSP_CTRL_CROSS) {
		printf("[X] pressed.\n");
		}

        else

        if (pad.Buttons & PSP_CRTL_CIRCLE) {
                printf("[O] pressed.\n");
                }
	}
        sleep(10); // idle for 10 milliseconds
}

```

---

### Post by Nerdriot on 2009-08-08
Man, I wanna thank you for that. I know I'll need that in the future. I've been trying to find some way to slow it down for a while, but never could find anything. Again, I'm still really new, so I'm glad you told me that.

My goal is to create a simple homebrew game, so this will be very beneficial to me later.

Thanks again! You've been awesome help :)

---

