---
title: "Python/Quickly - Set text in a textbox"
date: 2010-06-22
forum: Programming Talk
---

### Post by Admiral Yi on 2010-06-22
I'm using quickly to design a program, and just can't work out how to change the text in the textbox. This what I have so far:

```
    def search(self, widget, date=None):
        
        Searchbar = self.builder.get_object('Searchbar')
        keyword =  #This equals the text of Searchbar
       

        Dirchooser = self.builder.get_object('Dirchooser')
        directory =  #This must equal the current directory in the Dirchooser object
        

        Output = self.builder.get_object('Output')
        Output.set_text(commands.getoutput('ls -l ' + directory + ' | grep ' + keyword))
```

I have included the comments to show what I don't know how to do. I need to know the correct syntax for:

1) Saving the text of a Text Entry box as a variable ('keyword' in my code)
2) Saving the current directory in a directory chooser box as a variable ('directory' in my code)

Any help would be appreciated!

---

### Post by Admiral Yi on 2010-06-22
Anyone? All I need is a bit of syntax help.

---

### Post by towb on 2010-06-22
You probably want the .get_text() and get_current_folder methods. Just look in the [docs]("http://library.gnome.org/devel/pygtk/stable/").

---

### Post by Admiral Yi on 2010-06-22
Ah, thanks! Couldn't find the docs myself, must have been searching for the wrong thing.

---

