---
title: "Some Python help please"
date: 2011-04-16
forum: Programming Talk
---

### Post by AVatch on 2011-04-16
Hi, I am having some trouble doing the following task:

I want to re-plot the below graph, given a set of data from a text file....but the points corresponding to higher redshifts should be redder and the points corresponding with lower redshifts should be bluer.
[IMG]https://files.nyu.edu/akv224/public/NoiseRedshift_u.png[/IMG]

Does anyone know how I can do this?

Thanks!

---

### Post by simeon87 on 2011-04-16
You have to change the color of a circle based on its y-coordinate. I don't know what library you're using to draw the plot but you should look up how to change the drawing color. It's most likely a RGB color (red/green/blue) and you can change the values of each color component (i.e., a little more red, a bit more blue).

---

### Post by AVatch on 2011-04-16
> **simeon87 said:**
> You have to change the color of a circle based on its y-coordinate. I don't know what library you're using to draw the plot but you should look up how to change the drawing color. It's most likely a RGB color (red/green/blue) and you can change the values of each color component (i.e., a little more red, a bit more blue).

I am using matplotlib, and yes that was my idea originally to do something like

[x, 0.5, 1.-x] where x = redshift / max(redshift). But the thing is I don't know how to define the colors by RGB values.

as in I am not sure how to say...

Color c = [0.75, 1, 0.5]

and then plot it using c as the color of the point.

I looked for examples but I cant find anything useful.

---

