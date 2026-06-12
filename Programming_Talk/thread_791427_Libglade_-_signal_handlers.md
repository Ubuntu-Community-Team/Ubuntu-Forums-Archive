---
title: "Libglade - signal handlers"
date: 2008-05-12
forum: Programming Talk
---

### Post by n000b on 2008-05-12
Hi,

I'm trying to develop a program using libglade and I have run in to a question that I can't find an answer to (the libglade documentation is reasonably non-existant by the looks of it). I am trying to use custom signal handlers, so that when I press a button on the interface, it will call a custom function. I need to pass data (just a custom string for each button) in to the custom function, but I'm not sure what parameters I need my custom function to accept, and I'm also not sure what to do in Glade to pass that data in.

Please help :)

---

### Post by kknd on 2008-05-12
I preffer to use plain GTK, like:

g_signal_connect(button, "clicked", G_CALLBACK(func), userdata);

Where userdata will be the custom parameter.

---

### Post by MicahCarrick on 2008-05-12
With libglade (as opposed to GtkBuilder in GTK+ 2.12 and better) there are 2 ways we typically connect callback functions to signals (3 ways if you count using g_signal_connect as previously mentioned).

First, in Glade, you specify a "handler" for the various signals available for a widget. For reasons you'll see in a minute, this "handler" you specify should match the name of the function you will create as the callback function for that signal.

Then, to connect you callback function to that "handler", you can either use glade_xml_signal_autoconnect() (if you aren't passing custom data or are passing the same data to each function) or using glade_xml_signal_connect.

I prefer using glade_xml_signal_connect() since it allows me to pass different data to my different callbacks and it doesn't require using the -export-dynamic option when compiling.

So, as an example, let's say you have a GtkButton in your glade file. Using the 'Signals' tab of the 'Properties' pane, you can specify a handler called 'on_button1_clicked'. 

Next, in your source file, you would define a function for this "clicked" signal. You know what this function should look like because the prototype is in the API documentation for a GtkButton under "Signals".

```
void on_button1_clicked (GtkButton *button, gpointer user_data)
```

Now let's say that the user data that you want to pass is a GtkEntry you have already setup. You can then connect the callback to the signal using:

```
glade_xml_signal_connect_data (xml, "on_button1_clicked",
        G_CALLBACK (on_button1_clicked), entry);
```

This function's arguments:
[LIST]
[*]xml - The GladeXML object
[*]"on_button1_clicked" - this is the handler name as you specified in Glade.
[*]G_CALLBACK (on_button1_clicked) - This is the function callback you defined in the source code just above.
[*]entry - This is a GtkEntry you initialized previously to pass to the callback function.
[/LIST] 

If you want to pass more than one object to a callback function as user_data, you can pass a struct as shown in this example: [http://www.gtkforums.com/about906.html]("http://www.gtkforums.com/about906.html")

If you want a bit more information, I have a tutorial on using Glade 3 here: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

### Post by n000b on 2008-05-12
Thanks for the help guys.

I'm trying to make a point of sale interface, where there will be a number of buttons (Item 1, Item 2, Item 3 for sale etc). I do not know how many buttons, or the names of the buttons there will be (as I would like to leave the GUI customisable), which is why I was interested in using glade_xml_signal_autoconnect(). I was planning on making all of the buttons use the same function for their signal handler, and using the "User Data" field to send a different string of text depending on the button - is this possible to send a different string to the same function for all the buttons?

I am open to using glade_xml_signal_connect() and manually specifying each button IF there's a way for me to get a list of buttons - but I'm not sure if there is.

Thanks again for the help :)

---

### Post by MicahCarrick on 2008-05-12
Yes, you can use a single callback for any number of buttons. However, glade_xml_signal_autoconnect() doesn't allow you you to pass user_data and the user_data field in Glade only supports objects in that same glade file. Therefore, you will need to either use glade_xml_signal_connect_data() or define your own signal connect function and user glade_xml_signal_autoconnect_full()

You will know which button was pressed by the first argument of the callback which is the GtkWidget initiating the signal.

---

### Post by n000b on 2008-05-21
Hmm, I've hit a bit of an issue. I'm trying to make a numpad (10 buttons labeled 0-9) - when a button is pressed, I want it to enter that number in to a Text View (or text entry, etc).

I would like to define only one function for them in my code.

I know that I could do something like this in my code:

```
glade_xml_signal_connect_data(xml, "insert_text_1", G_CALLBACK(insert_text), "1");
glade_xml_signal_connect_data(xml, "insert_text_2", G_CALLBACK(insert_text), "2");
glade_xml_signal_connect_data(xml, "insert_text_3", G_CALLBACK(insert_text), "3");
```

But I was kind of hoping I might be able to do it by only connecting one signal, so it is more portable.

Is there any way to do this only using one signal connect call? Perhaps I could get the number that needs to be inserted from the name of the button, but I'm not sure how I could do that.

---

### Post by slavik on 2008-05-21
> **n000b said:**
> Hmm, I've hit a bit of an issue. I'm trying to make a numpad (10 buttons labeled 0-9) - when a button is pressed, I want it to enter that number in to a Text View (or text entry, etc).

I would like to define only one function for them in my code.

I know that I could do something like this in my code:

```
glade_xml_signal_connect_data(xml, "insert_text_1", G_CALLBACK(insert_text), "1");
glade_xml_signal_connect_data(xml, "insert_text_2", G_CALLBACK(insert_text), "2");
glade_xml_signal_connect_data(xml, "insert_text_3", G_CALLBACK(insert_text), "3");
```

But I was kind of hoping I might be able to do it by only connecting one signal, so it is more portable.

Is there any way to do this only using one signal connect call? Perhaps I could get the number that needs to be inserted from the name of the button, but I'm not sure how I could do that.
shouldn't each button have it's own signal handler?

When programming a GUI, you have to realize that you are telling the button itself that it was clicked, not just calling some function when it's clicked.

---

### Post by n000b on 2008-05-21
> **slavik said:**
> shouldn't each button have it's own signal handler?

I'm not sure what you mean? Button 1 would have insert_text_1 as it's handler, button 2 will have insert_text_2 etc.

---

### Post by slavik on 2008-05-21
> **n000b said:**
> I'm not sure what you mean? Button 1 would have insert_text_1 as it's handler, button 2 will have insert_text_2 etc.
right, but then why do you need to pass info to the handlers since they know what button was pressed?

---

### Post by n000b on 2008-05-21
> **slavik said:**
> right, but then why do you need to pass info to the handlers since they know what button was pressed?

So you're saying that in my insert_text function I should do something like this (can you even compare widgets like this?):

```
if (widget == gtk_get_widget(xml, "button1")
{
     // insert "1" here
}
// etc
```

I guess I could do that, but I was hoping that there would be some way I could tell the program to enter from the glade side of things, so that my program is more expandable in that if I want to add a new number to be added, I just have to add the button in glade and set some parameters, but I don't have to touch my code.

---

### Post by slavik on 2008-05-21
you have a callback_button1() that gets called when the button with 1 gets clicked on. inside it, you get a reference to the text widget (the display of the calculator) and append the proper characters there.

ie: for every button, you will have a separate callback. or alternatively, you can even figure out what event and what widget caused you to be called. (I think)

---

