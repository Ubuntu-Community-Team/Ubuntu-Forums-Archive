---
title: "[C/C++] Motif Issue"
date: 2009-10-05
forum: Programming Talk
---

### Post by dwhitney67 on 2009-10-05
It's been over 10 years since I did X-Motif programming under Solaris, and now under Linux knowledge of how to develop widgets does not appear (no pun here) to be working.

Can someone with X-Motif experience assist me with figuring out why I cannot get one of my button-pulldown-menu widgets properly working.  If you compile the app below, you will notice that the left hand-side button-pulldown is not properly displayed.

Motif.c:
```

#include <Xm/Xm.h>
#include <Xm/MainW.h>
#include <Xm/Form.h>
#include <Xm/RowColumn.h>
#include <Xm/PushB.h>

#include <stdlib.h>


Widget createPulldownMenuButton(Widget parent, char** menuItems, int menuSize);

int main(int argc, char** argv)
{
   char* numbers[]    = {"One", "Two", "Three"};
   char* daysOfWeek[] = {"Monday", "Tuesday", "Wednesday"};

   XtAppContext app;
   Widget       topLevel = XtVaAppInitialize(&app, "Test", NULL, 0, &argc, argv, NULL, NULL);
   Widget       window   = XmCreateMainWindow(topLevel, "main_window", NULL, 0);
   Widget       form     = XmCreateForm(window, "form", NULL, 0);

   Widget button1 = createPulldownMenuButton(form, numbers,    sizeof(numbers)    / sizeof(char*));
   Widget button2 = createPulldownMenuButton(form, daysOfWeek, sizeof(daysOfWeek) / sizeof(char*));

   XtVaSetValues(button1, XmNtopAttachment,    XmATTACH_FORM,
                          XmNleftAttachment,   XmATTACH_FORM,
                          XmNbottomAttachment, XmATTACH_FORM,
                          NULL);

   XtVaSetValues(button2, XmNtopAttachment,    XmATTACH_FORM,
                          XmNleftAttachment,   XmATTACH_WIDGET,
                          XmNleftWidget,       button1,
                          XmNrightAttachment,  XmATTACH_FORM,
                          XmNbottomAttachment, XmATTACH_FORM,
                          NULL);

   XtManageChild(window);
   XtManageChild(form);

   XtRealizeWidget(topLevel);

   XtAppMainLoop(app);
}

Widget createPulldownMenuButton(Widget parent, char** menuItems, int menuSize)
{
   int n = 0;
   Arg args[20];

   XtSetArg(args[n], XmNhighlightThickness, 0); ++n;
   XtSetArg(args[n], XmNshadowThickness,    0); ++n;

   Widget option   = XmCreateOptionMenu(parent, "foo", args, n);
   Widget button   = XmOptionButtonGadget(option);
   Widget pulldown = XmCreatePulldownMenu(option, "pulldown", NULL, 0);

   Widget* optionButton = malloc(menuSize * sizeof(Widget*));

   for (int i = 0; i < menuSize; ++i)
   {
      n = 0;
      XmString string = XmStringCreateSimple(menuItems[i]);
      XtSetArg(args[n], XmNlabelString, string); ++n;

      optionButton[i] = XmCreatePushButton(pulldown, "opt_but", args, n);
      XmStringFree(string);

      XtManageChild(optionButton[i]);
   }
   free(optionButton);

   n = 0;
   XtSetArg(args[n], XmNsubMenuId, pulldown); ++n;
   XtSetValues(button, args, n);

   //XtManageChild(button);
   //XtManageChild(pulldown);
   XtManageChild(option);

   return option;
}

```

Makefile:
```

EXE      = motif

SRCS     = Motif.c
OBJS     = $(SRCS:.c=.o)

CFLAGS   = -Wall -pedantic -ansi -std=gnu99 -c

LDFLAGS  = -L/usr/X11R6/lib
LIBS     = -lXm -lXt -lX11

all: $(EXE)

$(EXE): $(OBJS)
        $(CC) $^ $(LDFLAGS) $(LIBS) -o $@

.c.o:
        $(CC) $(CFLAGS) $<

clean:
        $(RM) $(OBJS) $(EXE)

```

---

### Post by dwhitney67 on 2009-10-08
Bump.

---

