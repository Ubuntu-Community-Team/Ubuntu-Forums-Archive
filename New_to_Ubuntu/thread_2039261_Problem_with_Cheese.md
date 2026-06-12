---
title: "Problem with Cheese"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Lingadharini on 2012-08-08
I installed Cheese, the webcam software for my lucid with the terminal command sudo apt-get install cheese.
When I start up the cheese, it says 'One or more needed GStreamer elements are missing: gconfaudiosrc, gconfvideosink.' with a help button.
Clicking the help button opens the FAQ page and it doesnt say anything about the elements the Cheese speaks about.
I tried searching for the said elements in synaptic package manager. That too didnt provide the expected results.
Please tell me what I can do..:(

---

### Post by Lingadharini on 2012-08-08
Thanks everyone, I got it working..
Did a 
sudo apt-get install gstreamer0.10-gconf
and everything is fine..
Thanks

---

