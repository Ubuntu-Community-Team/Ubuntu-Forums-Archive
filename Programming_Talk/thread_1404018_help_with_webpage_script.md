---
title: "help with webpage script"
date: 2010-02-10
forum: Programming Talk
---

### Post by woodmaster on 2010-02-10
Hello.  We recently took over control of a webpage from a previous webmaster and have a very limited knowledge of the scripting involved in web design.  So we are learning on our feet.  The webpage is: [http://www.thefallfrolic.com]("http://http://www.thefallfrolic.com").  The particular page we are having a major problem with is: [http://www.thefallfrolic.com/Music.htm]("http://http://www.thefallfrolic.com/Music.htm").  So, we want to eliminate all that white space on there between the **[FONT=Times New Roman]_FRIDAY NIGHT-SEPTEMBER 17th, 2010 _[/FONT]**[FONT=Times New Roman][SIZE=2]header and the [/SIZE][/FONT][SIZE=5]**Nadine, Beautiful Shining **[SIZE=1]/top of the pictures section.  So how to do this?  Everything we've tried has broken it.  the relevant section of code is:
[/SIZE][/SIZE]```

 <tr>
    <td width="682" valign="top" align="left" height="1148">
      <div align="left">
        <table border="0" width="682" align="left" cellpadding="5">
          <th><tr><td width="482">
              <p align="center"><b><i><font size="6" face="Times New Roman">Musical Guests
              And Entertainment</font></i></b></p><p align="center"><font face="Times New Roman" size="3"><i><b>All</b>
              festival entertainment & music is included in <b>Weekend
              Passes</b> and <b>Day</b> <b>Passes</b>. <br>However if you choose to <b>JUST</b>
              show up for the concert and evening drum circle you can purchase <b>Concert
              Passes</b> for <b>$10</b> each. 
               See rates for more information.</i></font></p></th>
              <p align="center"><b><font face="Times New Roman"><u>FRIDAY NIGHT-SEPTEMBER 17th, 2010</u></font></b></p>
              <table border="0" width="100%" height="0">
                  <td width="100%" valign="top"><p align="center"><font size="5"><b>Nadine, Beautiful Shining Woman <br>& Kokopelli</font></b><br>
                  <font size="3"><b>Performing 8pm-9pm in the Main Lodge </b><br>(after Kickoff Karaoke)</font> </p><br>
                  <td width="100%" valign="top" height="0">
                  <p align="center"><img src="[./images/nadineearthvisionweavers.jpg]("http://ubuntuforums.org/view-source:http://www.thefallfrolic.com/images/nadineearthvisionweavers.jpg")" width="125" height="250" border="0" ><img border="0" src="[./images/kokopelli.jpg]("http://ubuntuforums.org/view-source:http://www.thefallfrolic.com/images/kokopelli.jpg")" width="175" height="250">
                  <br>
                 <a href="[http://www.myspace.com/earthvisionweavers]("http://ubuntuforums.org/view-source:http://www.myspace.com/earthvisionweavers")">www.myspace.com/earthvisionweavers</a><br>
                 <a href="[http://www.myspace.com/kokopelligi]("http://ubuntuforums.org/view-source:http://www.myspace.com/kokopelligi")">www.myspace.com/kokopelligi</a><br>
                  </p></td>
                  <tr>
                  <td width="100%" valign="top" height="0">
                    <p align="center">Original pagan music with Nadine,
                    Beautiful Shining Woman <br>and Kokopelli!<br>
                    Enjoy original songs plus traditional pagan music - vocals
                    and guitar, Celtic harp, Native American flutes, drums, and
                    percussion.<br>
                    Nadine: beautiful vocals plus Celtic harp, drums, &
                    flutes<br>
                    Kokopelli: singer/songwriter & guitarist!<br>
                    With Nadine and Kokopelli together, these songs <br>have never
                    sounded so good!
                  </td><tr><td width="100%" height="84">
                  <p align="center"><font size="5"><b>Obi Kaye</b></font><br>
                  <font size="3"><b>Performing 9pm-10pm in the Main Lodge <br>& staying for Frolic Fire this year!</b></font>
                </td>
                  <td width="100%" valign="top" height="228">
                  <p align="center"><img width="240" align="center"height="271" border="0"src="[./images/ObiKayemusicpage.jpg]("http://ubuntuforums.org/view-source:http://www.thefallfrolic.com/images/ObiKayemusicpage.jpg")"<br>
                 <br> 
                 <span><a href="[http://www.shaved-monkey.com]("http://ubuntuforums.org/view-source:http://www.shaved-monkey.com/")">www.shaved-monkey.com</a></span>&nbsp;<br>

```

---

### Post by amsterdamharu on 2010-02-11
When I open your page and view source I see a bunch of <br><br> in there. But the source you posted doesn't have that.

---

### Post by Paddy Landau on 2010-02-11
Your two tables are all mixed up, and this is probably confusing the browser.

If you don't know HTML, you may be better off using a program that will do the HTML for you, instead of doing it yourself. I don't know of any free ones, but I know they're out there.

Otherwise take a careful look at the [HTML specifications for elements]("http://www.w3.org/TR/html4/index/elements.html"), and follow it carefully.

Good luck.

---

### Post by woodmaster on 2010-02-11
thanks guys...downloaded Seamonkey to use the Composer feature and it seems to be working good as a WYSIWYG.  Will mark this solved I guess...

---

### Post by Paddy Landau on 2010-02-12
> **woodmaster said:**
> downloaded Seamonkey to use the Composer feature and it seems to be working good as a WYSIWYG.
Excellent news.

When you're done, you'll probably want to check your website, at minimum, on Firefox, Opera and (on Windows) Internet Explorer, to make sure that it works OK.

---

### Post by woodmaster on 2010-02-12
yep...was planning.TY.

---

