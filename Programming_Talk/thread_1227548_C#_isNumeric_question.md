---
title: "C# isNumeric question"
date: 2009-07-30
forum: Programming Talk
---

### Post by Mirge on 2009-07-30
I can't recall where I read it... but I was google'ing around for a way to see if a value was numeric or not... basically the following are all "valid":

1.05
534
7,209.55

People had mentioned that there was no "built-in" C# method for determining if a particular value was numeric or not.

Is there anything dangerous or wrong about using something like:

```

bool isNumeric(string s)
{
     double tmp = 0;
     return double.TryParse(s, out tmp);
}

```

Thanks..

---

### Post by jero3n on 2009-07-30
It is just fine, it is my preferable solution.

You may see more ideas here
[http://www.codeproject.com/KB/cs/csharp-isnumeric.aspx](http://www.codeproject.com/KB/cs/csharp-isnumeric.aspx)

---

### Post by Mirge on 2009-07-30
> **jero3n said:**
> It is just fine, it is my preferable solution.

You may see more ideas here
[http://www.codeproject.com/KB/cs/csharp-isnumeric.aspx](http://www.codeproject.com/KB/cs/csharp-isnumeric.aspx)

Thank you kindly!

---

### Post by Mirge on 2009-07-30
Hmm.. another question if I may,

I've got:

```

        private void textInputNumber_KeyDown(object sender, KeyEventArgs e)
        {
            if (e.KeyCode.ToString() == "Back")
            {
                e.Handled = true;
                MessageBox.Show("got here");
                return;
            }
        }

```

What I'm trying to do is detect a backspace keypress, and stop it from doing what it'd normally do... just using backspace as an example. I'm building a very basic calculator app just to learn/practice, and I'll be disabling other keypresses, like letters.

How would I go about doing that? I get the popup message box, but it doesn't prevent it from doing a backspace.

---

### Post by Mirge on 2009-07-30
I was curious, so I displayed the value of textInputNumber.Text before & after the e.Handled = true statement... before, it is the original value before... and after the e.Handled = true statement, it's the new value.

I *could* just change it back to what it was, but I'd rather try to find out why it's actually continuing with the event when I set the e.Handled property to true...

EDIT:

```

        private void textInputNumber_KeyPress(object sender, KeyPressEventArgs e)
        {
            if (e.KeyChar == (char)Keys.Back)
            {
                MessageBox.Show("got here, canceling keypress.");
                e.Handled = true;
            }
        }

```

Changed the event handler to KeyPress instead, and the above works... in case anybody else was wondering.

---

### Post by jero3n on 2009-07-31
It's not a bug, it's a feature :D

[http://support.microsoft.com/kb/326442](http://support.microsoft.com/kb/326442)

Internally this event is to handle non alphanumeric keys and after that, KeyPress is also triggered which is finally responsible for control's text.

---

### Post by Mirge on 2009-07-31
> **jero3n said:**
> It's not a bug, it's a feature :D

[http://support.microsoft.com/kb/326442](http://support.microsoft.com/kb/326442)

Internally this event is to handle non alphanumeric keys and after that, KeyPress is also triggered which is finally responsible for control's text.

lol yeah, I had to do a bit of digging around to figure that out :)

---

