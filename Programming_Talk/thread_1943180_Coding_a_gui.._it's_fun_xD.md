---
title: "Coding a gui.. it's fun xD"
date: 2012-03-19
forum: Programming Talk
---

### Post by Stew822 on 2012-03-19
Hi everyone, 

not sure if I'm allowed to post this here; it's got absolutely nothing to do with ubuntu, but I couldn't find any other place that wasn't full of adds where I could discuss this. So, yeah, if it's in the wrong places/shouldn't be here, feel free to delete it or tell me so I can delete it (assuming the forum allows me too).

So anyway, I'm currently writing a GUI library in C++. That is, I started yesterday xD The layout and style of the gui is going to be in a file, and I'm currently designing the syntax for those files. It's going to be very HTML-like, I think, with a different file determining the style, much like CSS.

Ok. I admit it. I'm basically copying HTML and CSS. :guitar:

I'm aiming to create it so that all of the GUI programming is done through these files, instead of being done through C++. I haven't really decided how yet, but all of the "stuff" your program is going to do will be done through C++ or an interpreted language, probably python if I can get it working.

So anyway, back to the topic. Here's how I have the syntax now:
```

(boxlayout: root orientation:"vertical")
    (interchangeable: top_panel default:"view" )
        (gridlayout: view)
            
        (/gridlayout)
        (button text="helloooooo" /)
        
    (/interchangeable)
    
    (boxlayout: bottom_panel size_hint_y:0.1)
        (button) text:"This does nothing" on_press:say_hi() (/button)
        (text: the_folder) (/text)
        (boxlayout: bottom_panel_right) 
            (options: current_page default:"viewbutton")
                (option: viewbutton text:"view" height:0.2 on_press: swap_top_to_view() /)
                (option: organisebutton text:"organise"    on_press: swap_top_to_organise() /)
                (option: settingbutton text:"settings"     on_press: swap_top_to_settings() /)
            (/options)
        (/boxlayout)
    (/boxlayout)
(/boxlayout)

```It's (TYPE: ID [name:value ...] /) and the ID is optional - but if you want access to that widget you have to supply an ID, or you might be able to do something like: root.interchangeable to get to the interchangeable widget (which is basically just a container that only displays one of it's children.)

I'm going for simplicity over power, but that's not to say that it won't be powerful when it's done. 

Anyway, what do you think of the syntax? Do you reckon it could be improved? I'm debating whether there should be a [name:value ..] section in the (widget) bit, and I'm trying to think of a better way to do it. I haven't come up with anything at the moment.

Anyway, most of the basics are in place and really, all I have left to do is finish the parser, implement the CSS-bit and add some more widgets.

edit: oh, and I'm calling it tage, for "Totally Awesome GUI Engine!". Eventually I want to create a "Totally Awesome Game Engine!" and when I do I'll probably merge them :)

---

### Post by hakermania on 2012-03-19
Nice :)
I don't have much to comment, I hope you good luck with this :)

---

### Post by juancarlospaco on 2012-03-19
Try QML

---

### Post by anewguy on 2012-03-19
You do realize GTK exists as well and runs in Windows and Linux?

I admire the willingness, and it will be a good learning experience for you, but after many years in this business the idea of using established existing tools gets too appealing.

Not to say they don't have their problems - I've run into some I get no help for.

But, things like GTK, and I'm sure there must be others I just don't know about, work in several languages.

You may also want to see the Glade developer tool.  I personally don't use it because I'm still trying to figure out how things actually work before I put a layer between how things work and myself.  However, it generates XML files - you may really want to check it out.

Dave ;)

---

### Post by schauerlich on 2012-03-19
Many other GUI frameworks use a similar approach - for example, Android and Cocoa/Cocoa Touch all use XML files for their layout. Rather than inventing your own language (and writing your own lexer/parser) it would be much simpler to just have your format use XML - you already admit it's similar to HTML, so it won't be that far off. And the nice thing about XML is that you get the syntax for free, leaving you to focus on implementing the semantics of the language. Also, there's a decent XML library available for just about any modern language, so potential users and tool developers can easily manipulate the file format you make.

---

### Post by Stew822 on 2012-03-19
Hmm, QML seems to be pretty cool. I've never heard of it before despite *numerous* searches looking for something similar to what I've embarked on. If I fail at this, I'll probably resort to it.

Yes, I've heard of GTK. It was the first thing I looked at. To be blunt, I don't like it. 

About the XML files, yeah, I was considering using them, but there are already numerous GUI libraries that use them, and quite frankly, I don't think the syntax will let me do what I'd like to do without a lot of tweaking. 

Having had a look at QML, I think this would be a better syntax:
```

(vbox: root)
    background_color: #000000;
    (image)
        source: "~/image.jpg"
        scale: center
        height: 80%
    (/image)
    (hbox)
        (button %red_button) text: "show image" onclick: load_image() (/button)
        (label) text: "image: " (/label)
        (textfield) width: 80% (/textfield)
    (/hbox)
(/vbox)

```
It would end up with an image at the top and a small panel at the bottom with a button and textfield. Hopefully. xD

I'll continue on with this though unless I get bored of it, in which case I'll resort to something else. My final aim is going to be implementing a photo organiser (which I've already tried in PHP and Python... both projects failed xD).

---

### Post by Vaphell on 2012-03-19
i agree that xml is godawful when you need to write it by hand because it lacks readability but in general having a solution follow some existing standard is huge.
In fact i work all the time with in-house layer of abstraction on top of qt (its syntax is C-ish, with heavy use of {} blocks and prop=value; it even supports rudimentary inheritance) that allows for flexible real time layouts made of few basic qt layouts and dozen widgets with events and dynamic expressions to describe app logic.

One of main complaints of other coworkers who happen to touch it sporadically is that it doesn't follow any widespread standard and the knowledge surrounding it is more of the word-of-mouth kind. There are quite nice docs but in the meantime quite a few hacks were whipped up to overcome bugs and original limitations (goddamned multimedia web2.0 age feature creep) and and even the dev's mind boggles at the creativity of lowly peons hacking layouts up.
Obvious problems with own solution - text editors don't support it, you can't go to stackoverflow with your problems and automatic code generation is sometimes desired (it's much easier when there are tools readily available)

---

### Post by anewguy on 2012-03-20
Back in the late 80's and early 90's we had a rad tool used purely for oracle databases and stored in oracle databases.  This was a large company, with extremely demanding time frames.  The rad tool essentially was a language unto itself to isolate you from the underlying code that was generated (usually COBOL or C) and the underlying hardware.  But there are always tradeoffs.  When you took some young kid fresh out of college with no knowledge of the underlying language and hardware, you got people writing things that didn't know what the heck they were doing.  Performance suffered - both for the runtimes but also for programmer productivity.  Knowing the underlying language and hardware, I could make it do things that even the developers of the rad tool didn't know how to do.  They wanted to know so they could include in their rad tool.  I didn't want to - figured if I figured out so could they, but the company I worked for worked out discounts for each thing like that I came up with.

So the point?  GTK is not a friendly thing to try to learn - there is a complete lack of any real useful documentation and of samples.  Tools like Glade that generate the XML, do so because Glade also has runtime tools for implementing what's in the XML they generated in the development tool.  And guess what that runtime uses - GTK.

I'm not advocating GTK - I really have forced myself to use it and I don't like it a all.  Glade helps remove my exposure to 1 layer of the pie, but without an understanding of that layer.

There really is only so much abstraction that can be done - gui's have a lot in common - buttons, selectors, windows, dialogs,  A million ways could be developed to provide tools to work with those.  Personally, rather than work on another gui production tool, I would work on a rapid application development tool that also incorporates a good abstraction tool for the gui.  Concentrate on how to present complex things needed to program situations (not the gui, the applications) and do so in a simple, easy to use rad tool.  It can be done.  There are a limited number of these available, and to be honest, a tool like the old tool we had would be a wonderful addition today for anyone using relational database (not sure if there are any non-relational database engines left).  Working on such a tool and merging the gui development tool into it could be fun, and potentially (I know, open-source and all) a money generatofor someone selling such a tool to a business or a development house.

But most of all - you could work on your gui generator, then use it to start building the rad tool.  Best of both worlds! ;)  If I was younger I would jump on such a project.  I've thought about it for years but just never been able to convince myself to start.  I "paid my dues" a long, long, long time ago.  I haven't worked since 1994.  So, I'm a little selective on what I want to take on at my age.

don't want to discourage you, but those energies and excitement could better serve something other than another gui tool.

Best of luck on what ever you decide to try.

Dave ;)

---

### Post by anewguy on 2012-03-20
Hey -don't get me wrong.  If you have the skills to take a definition of a screen like that and actually paint the screen with what is requested and trap/follow signal handling, you would be wasting that skil to work on "yet another screen descriptor"  - as old time unix users would say, "yasp".

Putting those skills to work on a far larger project would be so much better. 

That is, of course, just my opinion.

Dave ;)

---

### Post by Stew822 on 2012-03-21
What you're saying is, in simple terms, is that there are enough GUI toolkits out there already, and that my time would be better spent on another project encompassing an area that hasn't had the same amount of attention? 

I half agree with you on that point, but I've come across no projects that I have the skills to work with (I'm more of a "lets get this ***** working" kinda guy than "oh, wait a second, YOU'RE NOT FOLLOWING STANDARDS" kind of guy) and that actually interests me. Got any particular suggestions? 

anyway, to update you, I've finished the parser (skipping the lexer) and it can now translate:
```

(vbox: root)
    (button) text: "press meeeeee!" onclick=say_hello() (/button)
    (hbox)
        (button) text: "1" (/button)
        (button) text: "2" (/button)
        (button) text: "3" (/button)
    (/hbox)
(/vbox)

```
into a layout, I'll try to reproduce it in ACSII:
```

_________________
|                                |
|    presss meeee!    |
|                                |
|````````|``````|````````|
|    1    |   2   |     3    |
|_____|____|_____|

```

and I hooked up the "onclick" to run a python file, but I'm going to change it all to be C++-based, I think, and give the user the option of trying to run a python file.

now to work on the style file, which is going to be really cool when it's done :)

---

### Post by anewguy on 2012-03-22
And so all of these are actual drawing on the screen not just line graphics?  Configurable borders?  Configurable text?  Configurable colors?  The buttons change somehow so you know you are pressing it?  No need to be contigous and packed as your example shows?  Free-flow text anywhere?  Images anywhere?  Tables?  Scrolling display and selection windows?  file selection tool?  font selection tool?  pop-down menuing?Configurable alignment by item/widget? Justification?  List handling?  Nested widgets - like a box within a box with buttons? vertical and horizontal boxes?  Menu bars?  Widget specific help?  Well, you probably get the hint.  

These are just the minimums a tool like this needs to provide.  If you've coded all of this, I'm sure some of us would want to take a look at what you've done, but what I'm saying is that if you have done all of that then you have basically re-written what every other GUI tool out there already provides.  If you've coded all of this then you have the talents to move into something much more productive with the chance of commercial success if you want it, or at least to contribute to the Linux world.

If you've done all of that, please post a link to somewhere where we can download everything that's needed to compile it on our systems and test it.  If you don't want that public knowledge, PM it to some of us.

Dave ;)

---

### Post by Stew822 on 2012-03-22
Yeah, when I get it working again (my little 'compile' script deletes the binary executable thing every time I run it... I need to work on it xD) I'll show you a screenshot; but it's basically just a few buttons in funky positions :)

Yeah, I know. The buttons have configurable text. You'll be able to set the colours (of everything). There'll be default styles. I was thinking of making a "border" style attribute thing; so that you can set a border around any widget (now that I think about it, it would probably be a good idea). 

hahahahaha!!!! The buttons don't change as of yet, but I already know how I'm going to program that. I'm still getting the styles working which is higher up on my list of things to do. 

You'll be able to put any widget anywhere by setting the x and y values; eg "(button) x: 42 y: 24 (/button)". I'm not sure how that'll affect the automatic positioning, but I think the button will just come out the flow. And there will be "labels" for text anywhere; I might also make a "text" widget for large chunks of text, or combine the two.

I know. I'm doing it because: a) I have a lot of spare time on my hands, and I mean a lot. b) Most other GUI toolkits I've tried to work with are far too complicated, in my eyes, than what they need to be (excluding FLTK, but as far as I'm aware that doesn't use an "automatic" layout). There was going to be a C, but I can't remember it.

I suppose I could try and sell it :-\"

I will, I'll send you all a link when I've finished the styles and added a few more basic widgets :)

---

### Post by llanitedave on 2012-03-22
Yours will get more complicated as it becomes more functional.  And there are some very good free ones already out there.

Just something to think about.

---

### Post by Stew822 on 2012-03-22
True, but hopefully I can limit some of that complexity. Which ones do you know of that are free and simple? I did look, I promise.

Anyway, here's a file:
```

(vbox: root)
    (button) text: "the top, scary button" (/button)
    (hbox)
        (button %red_button) text: "say hello" onclick: say_hello() (/button)
        (button /)
        (button /)
    (/hbox)
    (button) text: "-" (/button)
(/vbox)

```
and running that produces:
[IMG]http://img51.imageshack.us/img51/3888/screenshotqxh.png[/IMG]

---

### Post by llanitedave on 2012-03-22
Well sure, yours is nice and simple, because it handles only one window, and it uses precoded defaults for positioning, and it doesn't bind to any independent functions.

Once you start giving it the ability to produce a fully functional GUI, one that allows different kinds of dialog boxes, multiple frames, real control widgets, flexible positioning of controls, etc., you'll find you have to make more of their definition code explicit and accessible to the programmer, and your complexity will increase exponentially.

It's good to try for simplicity, clarity, and functionality all at once, and plenty of people end up with none of the above.  I think if you do it right you can pick any two.

---

### Post by Stew822 on 2012-03-22
I love how much faith you guys have in me xD

Here was what I was thinking to open a dialog:
```

(button: root)
    onclick: open_dialog()
(/button)

```then you'll have to define and register an open_dialog function:
```

void open_dialog( tage::application app ) {
    // not quite sure what goes here yet, but I'm sure it'll be good. Something along the lines of:
    // load a window, defined in the settings.tage file:
    tage::window win = app.open_window( "settings.tage" ); 
    win.center(); // centers window on screen
    win.center_on_application( app ); // centers it into the middle of our application
}
void main() {
    tage::application app;
    app.register_function( "open_dialog", open_dialog );
    app.parse( "layout.tage" );
}

```"... and it uses precoded defaults for positioning..."
That's why it uses precoded defaults for positioning. For simplicity.

"Once you start giving it the ability to produce a fully functional GUI,  one that allows different kinds of dialog boxes, multiple frames, real  control widgets, flexible positioning of controls, etc., you'll find you  have to make more of their definition code explicit and accessible to  the programmer, and your complexity will increase exponentially."
Of course it will. I'm going to try and prove you wrong, but whenever you make anything larger the complexity is always increased (I mean, generally speaking).

"It's good to try for simplicity, clarity, and functionality all at once,  and plenty of people end up with none of the above.  I think if you do  it right you can pick any two.     "
I disagree. Anyway, enough pointless arguing -- we'll actually see what happens when I finish it. If you want, you can help decide the syntax.

I was thinking, for the "style" files, it would go something like this:
```

button {
    border_width: 3px
    rounded: 5px
    border_colour: blue
    border_color : red  # note that there's two colour spellings... AUSSIE AUSSIE AUSSIE OI OI OI xD
    background_colour: black
}
%red_button {
    background_color: red
}

```Just like CSS xD

The only thing I'm not sure about is whether certain widgets should have their own style attributes available. For example, take the following layout:
```

(vbox)
    (button %red /)
    (image %red /)
(/vbox)

```What if images had their own attributes that buttons know nothing about? For example:
```
%red {
    color: red
    image_style: centered # OH DEAR. "button" hasn't got a clue what this means, but for an 
    # image, it means "zoom in 'til it's filling the screen
}
```Or, should I only let the users use attributes that can be applied to all widgets? Taking the previous layout again (except perhaps exchanging "image" for "rectangle":
```
%red {
    color: red
    background_image: "path_to_image"
    background_image_style: centered
}
```Now, both the button and the rectangle (or image) would both display the image in their background.

Which do you prefer or do you have a better solution?

[edit]
A better example would be:
```

(vbox)
    (button %red /)
    (hbox %red)
        (button /)
        (button /)
    (/hbox)
(/vbox)

```and the style:
```

%red {
    color: red
    padding: 10 # Oh dear. Are we referring to the padding around the hbox and button, 
    # or are we referring to the padding within the hbox (between the buttons)? Perhaps the padding could mean
    # different things for different widgets, but again, that confuses things. 
    # (cue lightbulb appearing on ma head)
    # You'd just to have to do %red button { padding: 10 } to get the effect of having padding between boxes. 

```Ok. I can't believe that didn't occur to me before. We'll just use widget-independent styles.

[another edit]
after much, and I mean MUCH, coding, I finally got the selectors to work in a similar way to the CSS selectors (ie. div p { style_definitions_here } ). It took.... a lot. I'm going away on a holiday tomorrow. So talk to you again in a week or so :)
when I get back hopefully I can finish the style bit, then we'll be pretty almost at the end of doing all the hard yakka and we'll (by we'll, I mean I'll) be able to code us some widgets!

---

### Post by llanitedave on 2012-03-23
Hey, I'm not trying to discourage you.  Your title, "...it's fun", says plenty.  Go for it.

I'm just trying to make you aware that the complexity of the other tools available is not because they're poorly designed or implemented.  Just be prepared to deal with it, as your own offering becomes more powerful.

---

### Post by Stew822 on 2012-03-31
Alrighty, so I had a wonderful holiday :) I had a cold though, which kinda was a bit annoying, but I did a lot of swimming, so that was fun.

Anyway, the selectors are finished, as far as I can tell. Now I'm working on implementing some container widgets and working out how the width of the child widgets should affect the positioning.

I'm also debating whether or not to allow users to specify more than just styles in the "style file" (we need to come up with a name... that's so, I dunno, *wrong*). For example, I'm writing an example layout file (to see if it will work as I'm intending it to; and to figure out any bugs I hadn't thought of. It's mostly pseudo code.). Here's a section of it:

```

(tab) name: "organise"
    (vbox)
        (hbox) (label) text: "folder to store pictures in: " (/label) (textinput) onchange: save_settings() (/textinput) (/hbox)
        (hbox) (label) text: "how you'd like said folder to be organised*: " (/label) (textinput) onchange: save_settings() (/textinput) (/hbox)
        (hbox) (label) text: "how you'd like the images to be named*: " (/label) (textinput) onchange: save_settings() (/textinput) (/hbox)
        (hbox) (label) text: "what's your favourite colour?: " (/label) (textinput) onchange: save_settings() (/textinput) (/hbox)
        (hbox) (label) text: "what's your second favourite colour?: " (/label) (textinput) onchange: save_settings() (/textinput) (/hbox)
    (/vbox)
(/tab)

```
There is a lot of repetition going on there, so I was wondering if you'd think it would be better if it was just done like this:
```
(tab) name: "organise"
    (vbox)
        (hbox) (label) text: "folder to store pictures in: " (/label) (textinput %settings) (/hbox)
        (hbox) (label) text: "how you'd like said folder to be organised*: " (/label) (textinput %settings/) (/hbox)
        (hbox) (label) text: "how you'd like the images to be named*: " (/label) (textinput %settings/) (/hbox)
        (hbox) (label) text: "what's your favourite colour?: " (/label) (textinput %settings/) (/hbox)
        (hbox) (label) text: "what's your second favourite colour?: " (/label) (textinput %settings/) (/hbox)
    (/vbox)
(/tab)
``` 
with a "style" file like this:
```

%settings {
    onchange: save_settings()
}

```

Or, perhaps the style should be inline, so it's all in the one spot? I suppose I could make it an option, anyway. 

I was also wondering if you think it would be better if you had to specify the window, eg.
```

(window: root)
    title: "a happy day in the sun"
    (image) source: "ahappyday.jpg" (/image)
    (button) onclick: show_dialog() (/button)
    on_exit: shutdown()
(/window)

```

Another thing I was thinking is that we could make dialogs inline; eg, this could be below the code above:
```

(window: dialog)
    (label) text: "Press OK to do nothing, and press cancel to exit." (/label)
    (hbox)
        (button) text: "ok" (/button) (button) text: "cancel" (/button)
    (/hbox)
(/window)

```

Last thing I wanted your opinion on: should the markup language include functions? Instead of writing out a whole function for displaying a window like in the example above, perhaps I could provide a builtin function called "show" that opens a window. So you'd replace "onclick: show_dialog()" with: "onclick: show( "#dialog" )", or something similar.

---

