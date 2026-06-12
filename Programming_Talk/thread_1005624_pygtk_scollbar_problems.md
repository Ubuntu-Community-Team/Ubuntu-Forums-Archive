---
title: "pygtk scollbar problems"
date: 2008-12-08
forum: Programming Talk
---

### Post by jworr on 2008-12-08
I'm using a vscrollbar and I want to determine if the user has scrolled to the very bottom.  After reading through the pygtk reference, I tried using get_adjustment() then checking if "upper" and "value" were the same.  However, "upper" is always much greater than the "value" when the scrollbar is maxed.  Does anyone have any insights into this?  I just want to determine if a scrollbar is all the way at the bottom.

---

