---
title: "create openoffice document using python"
date: 2010-11-26
forum: Programming Talk
---

### Post by surfer on 2010-11-26
i am trying to create an openoffice document with python. without starting openoffice. the document is simple; a picture and a table more or less.

i can easily create the document so far (i haven't bothered yet to create the correct word and character count). when i open the document with openoffice it says that it's corrupt. that's understandable as i didn't fix the word and character count yet.

but the thing i do not know how to do right is how to name the image. the image name seems to contain some kind of checksum or something. it opened a valid document, changed the filename of the picture slightly, made the according changes in the contents.xml, zipped and reopened it. openoffice reporded the file as corrupt, fixed it, and the name of the picture was changed back to its original name.

does anybody have an idea how openoffice names the pictures it includes? i googled for some time but didn't find the relevant description yet.

or is there a python library that can create openoffice documents? should i look into pyuno?

---

### Post by juancarlospaco on 2010-11-26
Pyuno, your best bet...

---

### Post by surfer on 2010-11-26
as far as i understood, pyuno needs a running openoffice. is there no way to create an openoffice document without having to start openoffice itself?

with pyuno i have to interact with openoffice as far as i understood. i'd like to avoid that...

unfortunately [ooolib]("http://ooolib.sourceforge.net/") is nowhere near usable...

---

### Post by Cheesehead on 2010-11-26
You have three options to create .odt (OO Writer) files using Python. I have used all three.

OPTION 1: Use Python to directly manipulate the .odt XML. Your script must unzip the .odt template file, do a search-and-replace of the content.xml to customize the document, then zip the final renamed .odt.

This is best for simple paragraph text search-and-replace. You cannot create new content like inserted images or different fonts or changed margins that were not already in the template - if a reference to the image or font is not already in the settings.xml or styles.xml, then the unreferenced content will cause an error when you try to open the finished document in OpenOffice.

A workaround is to create references to everything you need in the template file. Add them all on the page using OO, and save the .odt, then go in manually and remove all the relevant content.xml. Or create a template that your script simply deletes excess from (instead of adding to).


OPTION 2: Use an intermediary like Odtwriter ([http://docutils.sourceforge.net/docs/user/odt.html]("http://docutils.sourceforge.net/docs/user/odt.html")) to create the final .odt file. Use python to create a simpler document that the intermediary can understand. 

This is good for simple documents. It starts to fall apart when you get into multiple images, margins, and precise formatting. Odtwriter is included in the 'python-docutils' package in the Ubuntu repositories.


OPTION 3: Pyuno. Directly using the OpenOffice engine to create and read documents is the most powerful and precise way to create complex documents and valid .odt files. It takes about a day or two to cobble together a script to create useful files (mostly due to the lousy documentation), and complex document scripts can run to a couple hundred lines of code.

For example, I have a script that creates invoices based on a dict pulled from a database - the OO-uno part is about 200 lines of code, including inserted images, custom tables, custom pararaph margins, a splashy header, etc. It took two days to figure it out, but now uno makes sense to me. It creates forty pages of invoices in about 20 seconds. It's not the way I'd write it normally, but a human will look over the finished invoices and she wanted the option of editing them in OO.

The 'python-uno' package is included in the Ubuntu repositories.A very good initial tutorial as at [http://lucasmanual.com/mywiki/OpenOffice]("http://lucasmanual.com/mywiki/OpenOffice") - it will save you 6 hours of frustration, including how to start a headless OO to work in, which takes much less resources. A great place to ask questions and search for prior answers is at [http://www.oooforum.org/]("http://www.oooforum.org/"). The reference uno API (*almost* helpful) is at [http://api.openoffice.org/docs/common/ref/com/sun/star/module-ix.html]("http://api.openoffice.org/docs/common/ref/com/sun/star/module-ix.html")

---

### Post by surfer on 2010-11-27
Cheesehead, thanks a lot!

i will look into that. especially odtwriter looks promising.

what i did so far is your first option. i have a jinja2 template i edit...

what i just found and will look into is [ODFPY]("http://odfpy.forge.osor.eu/"). can't say much about it yet...

---

