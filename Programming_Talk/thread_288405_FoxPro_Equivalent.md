---
title: "FoxPro Equivalent"
date: 2006-10-29
forum: Programming Talk
---

### Post by msimon1960 on 2006-10-29
I'm seriously considering moving to Ubuntu for my personal and professional OS.

I'm looking for Linux apps that will perform the same functions as my Windows apps.

1. OpenOffice will meet my Word, Excel, and PowerPoint needs.

2. I can run Frontpage under Wine -- is there another WYSIWYG web editor to consider?

3. I use a Contact Manager called ACT! 2007 -- is there something out there in Linux-world that will manage contacts, sales opportunities, and log all communication with contacts automatically (i.e. letter, emails, fax, phone)?  Everything I've seen has been web-based -- I want a database app to run on a local server.

4. I use Foxpro 5.0 for writing database apps.  I have zero interest in learning a low-level programming language and doing everything from scratch (been there so many times).  I want a dbase/foxpro like environment with forms designers, a programming language (some Basic derivative would be nice), and a report writer.  I don't care about the underlying database engine -- I write for personal or small workgroup use.

Thanking you in advance for any info provided!

Matthew.

---

### Post by nimrod_abing on 2006-10-29
> **msimon1960 said:**
> I'm seriously considering moving to Ubuntu for my personal and professional OS.

I'm looking for Linux apps that will perform the same functions as my Windows apps.

1. OpenOffice will meet my Word, Excel, and PowerPoint needs.

2. I can run Frontpage under Wine -- is there another WYSIWYG web editor to consider?

3. I use a Contact Manager called ACT! 2007 -- is there something out there in Linux-world that will manage contacts, sales opportunities, and log all communication with contacts automatically (i.e. letter, emails, fax, phone)?  Everything I've seen has been web-based -- I want a database app to run on a local server.

4. I use Foxpro 5.0 for writing database apps.  I have zero interest in learning a low-level programming language and doing everything from scratch (been there so many times).  I want a dbase/foxpro like environment with forms designers, a programming language (some Basic derivative would be nice), and a report writer.  I don't care about the underlying database engine -- I write for personal or small workgroup use.

Thanking you in advance for any info provided!

Matthew.

For #2, WYSIWYG HTML editing you can try nvu:

```
sudo apt-get install nvu
```nvu is use the Mozilla Gecko rendering engine (same one used by Firefox) so it's great for doing standards compliant designs.

For #3, I use a combination of both Evolution and GnuCash. Evolution is installed by default as part of ubuntu-desktop. GnuCash can be installed by:

```
sudo apt-get install gnucash
```GnuCash is a bit like Quicken and MS Money and you can import QIF files into it. It's got a bit of a steep learning curve if you haven't used financial management software before. Edgy comes with GnuCash 2.0 which has the Invoice and Billing functions that I found very useful. I suggest you read the help files for GnuCash before starting on a new account. Familiarize yourself with the interface and try creating a test account first before using it for actual business.

For #4, you can try Gambas which is really nice if you are familiar with Visual Basic. You can try it with the sqlite plugin for simple database-oriented apps:

```
sudo apt-get install gambas
```Although I have to admit it's a bit lacking in the report-generation functions but I think there is already work being done in that area. That said, I really  miss the good old days with Foxpro/Foxbase :)

HTH.

---

### Post by toojays on 2006-10-30
Does [Glom](http://www.glom.org/wiki/index.php?title=Main_Page) have any of the functionality which you miss from FoxPro?

---

### Post by nimrod_abing on 2006-10-30
> **toojays said:**
> Does [Glom]("http://www.glom.org/wiki/index.php?title=Main_Page") have any of the functionality which you miss from FoxPro?

Not that I'm knocking on Glom or anything but it looks like it's still in its infancy. It's also built from too many different pieces of software that there's a slight "glue-like" feel to it if you get my drift :) FoxPro has everything you need right there in one convenient package: forms designer, database designer, reports designer, debugger, etc.

Another thing is that Glom requires Postgres, while it's not a bad choice for the database backend, it's overkill for some projects. And in most cases, being able to move your database file around is a lot more convenient and easier to manage. This is where zero-config database solutions like sqlite, derby, hsql, and others come into play.

The thing I missed the most from FoxPro (in all it's incarnations) is the report designer. I think this part of a database programming suite has been undervalued and understressed. Being able to generate a WYSIWYG report is a really important thing for me. A lot of the solutions I've tried don't really come close to what FoxPro can do. The one that comes really close is JasperReports especially when coupled with [iReport]("http://jasperforge.org/sf/projects/ireport").

Also the integrated and graphical database designer found in Visual FoxPro is top-notch. Being able to visually design your tables and their relationships is really what makes for RAD part of things.

Another thing is the data-bound form controls. Not that this is difficult to implement but writing code over and over for displaying and working with data on forms is not a pleasant task. In Visual FoxPro at least (even in the DOS-based FoxPro) it's possible to drag-and-drop your table onto a form and you automatically get data-bound controls laid out for you.

At least at the moment, Gambas seems to have a head start on almost everything that FoxPro provides, with a VB-like environment and language to boot :) so it's currently the way to go if you're coming from the MS Visual <insert moniker here> stuff. The only thing missing is a visual database designer and visual report designer.

[http://gambasdoc.org/help/comp](http://gambasdoc.org/help/comp)

I guess it's safe to say that Gambas is really the "gold standard" when it comes to RAD tools on *nix right now.

---

### Post by msimon1960 on 2007-01-10
Thank you to everyone for their input -- I'll take a look at each of the apps mentioned.  Having input from experience Linux programmers sure helps lower the slope of the learning curve.

Matt.

---

