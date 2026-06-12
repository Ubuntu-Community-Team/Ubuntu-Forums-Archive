---
title: "could anyone help with html?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-26
I know this may not be the place but I can't find the solution to my problem
and I figured someone here must know how.

I am adding merriam-webster search to my custom home page.
I would like it to open the results in a new window but I can't figure out how to do it.

I have already tried   target="_blank"
but it just opens a blank window

this is the code
```
<!-- Merriam-Webster Searchbox Style 9 -->
            <script language="Javascript">
            function getValue(term){if(document.query.elements[0].checked == true){document.location.href = "http://www.merriam-webster.com/dictionary/" + term;}
            else if(document.query.elements[1].checked == true){document.location.href = "http://www.merriam-webster.com/thesaurus/" + term;}}
            </script>
            <form name="query" method="get" action="javascript:getValue(document.query.va.value)">
            <div style="margin:0;padding:0;border:solid 1px #000000;width:502px;">
            <div style="margin:0;padding:0;background-color:#dfe6ff;">
            <table cellpadding="0" cellspacing="0" style="margin:0;padding:0;font-family:Geneva,Arial,Helvetica,sans-serif;font-size:11px;font-weight:bold;color:#010066;">
            <tr>
            <td style="margin:0;padding:0;" width="150">
            <img src="http://www.merriam-webster.com/images/searchbox/hdr_500x32.gif" width="149" height="32" hspace="0" vspace="0" align="left" />
            </td>
            <td width="175" align="center" valign="middle" style="margin:0;padding:3px;vertical-align:middle;">
            <input type="radio" name="mySelect" value="Dictionary" checked>Dictionary
            <input type="radio" name="mySelect" value="Thesaurus">Thesaurus
            </td>
            <td width="175" valign="middle" style="margin:0;padding:3px;vertical-align:middle;">
            <input type="text" align="top" name="va" size="24">
            <input type="image" src="http://www.merriam-webster.com/images/searchbox/btn_go_19x18_blue_matte.gif" alt="Go" width="19" height="18" border="0" style="vertical-align:-25%;">     
            </td>
            </tr>
            </table>
            </div>
            </div>
            </form>
```
thanks for any help

---

### Post by Paqman on 2008-11-26
> **nakama85 said:**
> 
I have already tried   target="_blank"


That should work, but IIRC you'll fail W3C validation because of it.

That's some pretty horrendous looking code they've given you. Whoever wrote that needs a slap.

Out of interest, why does it *have* to open in a new window? The idea that people don't navigate back to your site is pretty discredited. People these days will quite happily use their back button.

---

### Post by nakama85 on 2008-11-26
> **Paqman said:**
> That should work, but IIRC you'll fail W3C validation because of it.

That's some pretty horrendous looking code they've given you. Whoever wrote that needs a slap.

Out of interest, why does it *have* to open in a new window? The idea that people don't navigate back to your site is pretty discredited. People these days will quite happily use their back button.

Its actually not for anyone but me.. I just rather close a window or tab then have to go back to my homepage after every search.

---

### Post by Paqman on 2008-11-26
> **nakama85 said:**
> Its actually not for anyone but me.. I just rather close a window or tab then have to go back to my homepage after every search.

Middle button (mouse wheel) in Firefox opens links in a new tab.

---

### Post by nakama85 on 2008-11-26
> **Paqman said:**
> Middle button (mouse wheel) in Firefox opens links in a new tab.

Apparently not on this search.... I just tried and nothing

---

### Post by Paqman on 2008-11-26
> **nakama85 said:**
> Apparently not on this search.... I just tried and nothing

Hmm, well if you're only trying to get the search box to open in a new tab then your problem isn't really HTML anyway, it's javascript. I don't know my **** from my elbow when it comes to js, but i'd say your problem is here:

```
{document.location.href = "http://www.merriam-webster.com/dictionary/" + term;}
```

To me, this looks like it's passing a URL to the browser made from the first part + the search term. Javascript can most certainly open new windows (!) but i'm not sure how you'd change the above to do so.

---

