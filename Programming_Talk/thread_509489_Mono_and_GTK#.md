---
title: "Mono and GTK#"
date: 2007-07-25
forum: Programming Talk
---

### Post by Lord Illidan on 2007-07-25
Hi guys/gals.

I am trying to learn more about mono and gtk#, and I've been looking at some internet resources to speed me on my way, yet I've come across a funny stumbling block.

On this site, [http://www.mono-project.com/GtkSharp:_Frames](http://www.mono-project.com/GtkSharp:_Frames), I found the following example.

[COLOR=#008080]*// frame.cs - Gtk# Tutorial example*[/COLOR]
[COLOR=#008080]*//*[/COLOR]
[COLOR=#008080]*// Author: Johannes Roith >johannes@jroith.de<*[/COLOR]
[COLOR=#008080]*//*[/COLOR]
[COLOR=#008080]*// (c) 2002 Johannes Roith*[/COLOR]
 
[COLOR=#0600FF]namespace[/COLOR] GtkSharpTutorial [COLOR=#000000]{[/COLOR]
        [COLOR=#0600FF]using[/COLOR] Gtk;
        [COLOR=#0600FF]using[/COLOR] [COLOR=#000000]System[/COLOR];
        [COLOR=#0600FF]using[/COLOR] [COLOR=#000000]System[/COLOR].[COLOR=#0000FF]Drawing[/COLOR];
 
 
        [COLOR=#0600FF]public[/COLOR] [COLOR=#FF0000]class[/COLOR] frame
        [COLOR=#000000]{[/COLOR]
 
                [COLOR=#0600FF]static[/COLOR] [COLOR=#0600FF]void[/COLOR] delete_event [COLOR=#000000]([/COLOR][COLOR=#FF0000]object[/COLOR] obj,
DeleteEventArgs args[COLOR=#000000])[/COLOR]
                [COLOR=#000000]{[/COLOR]
                Application.[COLOR=#0000FF]Quit[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
                [COLOR=#000000]}[/COLOR]
 
                [COLOR=#0600FF]public[/COLOR] [COLOR=#0600FF]static[/COLOR] [COLOR=#0600FF]void[/COLOR] Main[COLOR=#000000]([/COLOR] [COLOR=#FF0000]string[/COLOR][COLOR=#000000][[/COLOR][COLOR=#000000]][/COLOR] args[COLOR=#000000])[/COLOR]
                [COLOR=#000000]{[/COLOR]
 
                        [COLOR=#008080]*/* Initialise GTK */*[/COLOR]
                        Application.[COLOR=#0000FF]Init[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
    
                        [COLOR=#008080]*/* Create a new window */*[/COLOR]
                        Window window = [[COLOR=#008000]new[/COLOR]]("http://www.google.com/search?q=new+msdn.microsoft.com") Window [COLOR=#000000]([/COLOR][COLOR=#808080]"Frame
Example"[/COLOR][COLOR=#000000])[/COLOR];
  
                        [COLOR=#008080][I]/* Here we connect the "destroy" event to a
signal handler */[/I][/COLOR] 
                        window.[COLOR=#0000FF]DeleteEvent[/COLOR] += delete_event;
 
                        window.[COLOR=#0000FF]SetSizeRequest[/COLOR][COLOR=#000000]([/COLOR][COLOR=#FF0000]300[/COLOR], [COLOR=#FF0000]300[/COLOR][COLOR=#000000])[/COLOR];
                        [COLOR=#008080]*/* Sets the border width of the window. */*[/COLOR]
                        window.[COLOR=#0000FF]BorderWidth[/COLOR]= [COLOR=#FF0000]10[/COLOR];
 
                        [COLOR=#008080]*/* Create a Frame */*[/COLOR]
                        Frame frame = [[COLOR=#008000]new[/COLOR]]("http://www.google.com/search?q=new+msdn.microsoft.com") Frame[COLOR=#000000]([/COLOR][COLOR=#808080]"MyFrame"[/COLOR][COLOR=#000000])[/COLOR];
                        window.[COLOR=#0000FF]Add[/COLOR][COLOR=#000000]([/COLOR]frame[COLOR=#000000])[/COLOR];
 
                        [COLOR=#008080]*/* Set the frame's label */*[/COLOR]
                        frame.[COLOR=#0000FF]Label[/COLOR] = [COLOR=#808080]"GTK Frame Widget"[/COLOR];
 
                        [COLOR=#008080][I]/* Align the label at the right of the
frame */[/I][/COLOR]
 
                        frame.[COLOR=#0000FF]SetLabelAlign[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]([/COLOR][COLOR=#FF0000]float[/COLOR][COLOR=#000000])[/COLOR][COLOR=#FF0000]1[/COLOR].[COLOR=#FF0000]0[/COLOR],[COLOR=#000000]([/COLOR][COLOR=#FF0000]float[/COLOR][COLOR=#000000])[/COLOR][COLOR=#FF0000]0[/COLOR].[COLOR=#FF0000]0[/COLOR][COLOR=#000000])[/COLOR];
 
                        [COLOR=#008080]*/* Set the style of the frame */*[/COLOR]
                        frame.[COLOR=#0000FF]ShadowType[/COLOR] = [COLOR=#000000]([/COLOR]ShadowType[COLOR=#000000])[/COLOR] [COLOR=#FF0000]4[/COLOR];
 
                        frame.[COLOR=#0000FF]Show[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
  
                        [COLOR=#008080]*/* Display the window & all widgets*/*[/COLOR]
                        window.[COLOR=#0000FF]ShowAll[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
    
                        [COLOR=#008080]*/* Enter the event loop */*[/COLOR]
                        Application.[COLOR=#0000FF]Run[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
    
                [COLOR=#000000]}[/COLOR]
 
        [COLOR=#000000]}[/COLOR]
 
[COLOR=#000000]}[/COLOR]
Apart from the confusion in using frame as an identifier TWICE, it doesn't seem bad.  However, I get the following error when I run the program.

`Gtk.Frame' does not contain a definition for `SetLabelAlign'(CS0117)

Any ideas? In mono-doc, SetLabelAlign is mentioned...why is it not here?

---

### Post by Lord Illidan on 2007-07-25
Interestingly, [http://docs.gotmono.net](http://docs.gotmono.net) does not mention SetLabelAlign.

However, I have another question.

public [float]("http://docs.gotmono.net/display.aspx?url=ecma%3a%2f%2fgo%3flink%3dT%253aSystem.Single") **LabelXalign**   							{ 							 set; get;  							}

What does the set; get; mean?

---

### Post by Lord Illidan on 2007-07-25
Aha..it seems that either the tutorial is an old one or that it has been removed. Google Code Search revealed nothing for SetLabelAlign, but Xalign and YAlign do the same thing I guess.

Still, my previous question remains.

---

