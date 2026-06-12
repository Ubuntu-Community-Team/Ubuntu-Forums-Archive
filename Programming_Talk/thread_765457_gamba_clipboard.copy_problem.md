---
title: "gamba clipboard.copy problem"
date: 2008-04-24
forum: Programming Talk
---

### Post by nilsgn on 2008-04-24
Hi,

I'm a swedish 'old' man, 3/4 of my life I have progamming in VB6. Very nice.

Now I'm new in gamba looks well, but. There is some thing that confuce me.

And I want help not: "Switch to..."

In my project I have a TextBox that contains Swedish (åäöÅÄÖ).

This line: clipboard.copy(TextBox.text)
goes well.
But, when I paste it into a text document i lost the (åäöÅÄÖ)

If I from the TextBox, in the run program, select the text '(åäöÅÄÖ)' and Ctr+C (copy) and den paste it in to a text document I get my (åäöÅÄÖ)

I'm read that I can sett MIME type format for that Clipboard. I try some. But...

Can any explain this odd (in compare with VB6 in Windows, their this is no problem) behavior. Please! :confused:

Not: I find a workaround: Clipboard.copy(Conv(TextBox.Text, "utf-8", "Latin1"))
        But it is not the right way...

---

