---
title: "[Python] word wrap"
date: 2008-09-12
forum: Programming Talk
---

### Post by ipaqman23 on 2008-09-12
Hi,

i got a problem with a long string in Python - 

Script Snippet:

```
# get movie information from db
	movie = self.db.Movie.get_by(number=number)
	if movie is not None:
		if print_number == True:
			c.setFont(fontName, 10)
			c.drawCentredString(pageWidth/2, 530, number)

		c.setFont(fontName, 16)
		c.rotate(90)
		c.drawString(60, (-pageWidth/2)-8, movie.o_title.encode('utf-8'))
		c.rotate(-90)
		if movie.image is not None and movie.image != '':
			tmp_dest = self.locations['posters']
			image = str(os.path.join(tmp_dest, str(movie.image)+".jpg"))
			c.drawImage(image, x=(pageWidth-30)/2, y=470, width=30, height=50)
		# print movie info
		c.setFont(fontName, 8)
		textObject = c.beginText()
		textObject.setTextOrigin(pageWidth-cover_x, 500)
		textObject.setFont(fontName, 8)		
		textObject.textLine(_("Original Title").encode('utf-8')+': '+str(movie.o_title).encode('utf-8'))
		textObject.textLine(_("Title").encode('utf-8')+': '+str(movie.title).encode('utf-8'))
		textObject.textLine("")
		textObject.textLine(_("Director").encode('utf-8')+': '+str(movie.director).encode('utf-8'))
		textObject.textLine("")
		textObject.textLine(_("Running Time").encode('utf-8')+': '+str(movie.runtime).encode('utf-8')+ _(" min").encode('utf-8'))
		textObject.textLine(_("Country").encode('utf-8')+': '+str(movie.country).encode('utf-8'))
		textObject.textLine(_("Genre").encode('utf-8')+': '+str(movie.genre).encode('utf-8'))
		textObject.textLine("")
		textObject.textLine(_("Handlung").encode('utf-8')+': '+str(movie.plot).encode('utf-8'))
		c.drawText(textObject)
		# draw bigger poster image
		if poster == True and movie.image is not None:
			c.drawImage(image, x=(pageWidth-(pageWidth-cover_x)-235), y=(pageHeight/2)-125, width=180, height=250)
	c.showPage()
	c.save()
	self.widgets['print_cover']['window_simple'].hide()
	cover_file = os.path.join(self.griffith_dir, "cover.pdf")
```


Problem:
Variable movie.plot is very long and the script prints just one very long line - not very appealing! 

So how can I force word wrap for this string??

---

### Post by mike_g on 2008-09-12
First hit on google came up with this: 
[http://code.activestate.com/recipes/148061/](http://code.activestate.com/recipes/148061/)
Edit: lol, its got a -1 rating tho so its probably not all that great

Edit2: second hit might be better: 
[http://www.saltycrane.com/blog/2007/09/python-word-wrap-function/](http://www.saltycrane.com/blog/2007/09/python-word-wrap-function/)
Although you might want to search for a function with a justified option; looks much nicer IMO

Edit3: apparently theres a textwrap function in the standard library too:
[http://docs.python.org/lib/module-textwrap.html](http://docs.python.org/lib/module-textwrap.html)

---

### Post by Glaxed on 2008-09-12
If you don't feel like wasting your time, here's a little nugget that does the job nicely;

```

# python
def print_plot(text):
	if len(text) < 76:
		print text[:76]
		print_plot(text[77:])
	else:
		print text

```

If you want shorter lines, then replace "76" with the amount of chars you want per line. Change "77" accordingly. You could add a 'width' argument if you wanted to get all fancy.

---

### Post by mike_g on 2008-09-12
```
# python
def print_plot(text):
	[COLOR="DarkRed"]if len(text) < 76:[/COLOR]
		print text[:76]
		print_plot(text[77:])
	else:
		print text
```
Erm, are you sure thats right? And the width may also be better as a parameter.

---

### Post by Glaxed on 2008-09-13
Mmmhmm, right you are, I flipped the "<" sign. Here's the corrected one;

```

def print_plot(text, width):
   if len(text) > width:
      print text[:width]
      print_plot(text[width+1:])
   else:
      print text

```

---

### Post by ghostdog74 on 2008-09-13
> **Glaxed said:**
> Mmmhmm, right you are, I flipped the "<" sign. Here's the corrected one;

```

def print_plot(text, width):
   if len(text) > width:
      print text[:width]
      print_plot(text[width+1:])
   else:
      print text

```

your print_plot takes in 2 arguments. your script will get an error.
Also, please take your function on an actual text file and see if you get the correct results.

---

### Post by pp. on 2008-09-13
> **Glaxed said:**
> Mmmhmm, right you are, I flipped the "<" sign. Here's the corrected one

I do not object to recursive solutions as a matter of principle. However, given the way Python works and given the minuscule complexity of the problem, I think that an iteration would be preferable.

---

### Post by ipaqman23 on 2008-09-13
A friend of mine found the following solution which looks pretty elegant:

```
from textwrap import wrap 
		plot_string = str(movie.plot) 
		plot_string_newline = '\n'.join(wrap(plot_string, 80))
		textObject.textLines (str(plot_string_newline).encode('utf-8'))
```

But now it appears a new problem - what is when the string is too long and overlaps the cover? Is there a substring function in Python? Replace string from char ## with "..."?

---

### Post by mike_g on 2008-09-13
You could remove any lines after a set limit to constrain it to you container, or you could create a viewport of the area you are drawing to.

---

