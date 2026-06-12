---
title: "Problem with images (C++ gtkmm)"
date: 2007-04-21
forum: Programming Talk
---

### Post by shador on 2007-04-21
Im using C++ with GTKmm at the moment. 

What I've done is created a button and added an image and text to it like so: 

```
m_button.add_pixlabel("gaim.png", "cool button");
```

what I would like to do is to change the image when the button is clicked. Can I do that.? What I tried doing was using a fuction that got activated when the button got clicked and just entered the same command in that function but with a different image name. You guys get me? 

So in that function i entered the command

```
m_button.add_pixlabel("gaim-image.png", "cool button");
```

But that didn't work so what can I do instead?

---

