---
title: "Error in php script, so simple to find, so hard to resolve"
date: 2009-05-31
forum: Programming Talk
---

### Post by masux594 on 2009-05-31
hi everyone, i have a problem with a web&#8722;site developed by me.. i'm using a local LAMP server, and i've never seen en error like this.. as the title say, the error is simple, but i don't know where to fin solution..

```

  [.. some php code ..]
  echo "<p> some text, without quotes or other special characters <&#8725;p>";
  [.. other php code ..]

```

until there there's nothing wrong.. but, when i display the page[firefox], the result is :
" text <&#8725;p>" and if i inspect using firebug, it shows me the html code as 
" <p> text <&#8725;p><&#8725;p>"

Only one question, am i stupid or the stupid is the pc?

P.s. Using Netbeans 6.5.1 with JDK 6u13 x64 on Jaunty x64!

Sysc A

---

### Post by tturrisi on 2009-05-31
post the actual code so we can see just how simkple the fix is!

---

### Post by masux594 on 2009-05-31
here's the code!  

[HTML]<p> asdasd <&#8725;p>[/HTML]

 well when i analyze with firebug it shows this structure

---

### Post by masux594 on 2009-05-31
tnx for the reply.. well.. i worked on the web site all the afternoon[italy].. using Netbeans sometimes when i write some code tells me 'Unmatched tag'.. 
example: 
[HTML]<p> asdasd <&#8725;p>[/HTML] 
and in this line it shows the warning and if i display the page firebug display the html code as [HTML]<p> asdasd <&#8725;p><&#8725;p>[/HTML]
when i delete the "<&#8725;p>" that I wrote and call the auto&#8722;complete function in NetBeans, he add in the same fuc***g position the same string but when i display the page, firebug display the right html code !!
[HTML]<p> asdasd <&#8725;p>[/HTML]
maybe a NetBeans settings, but i don't modify nothing in the settings in this week&#8722;end and yesterday was ok!

Thank u!
Sysc A

---

### Post by Reiger on 2009-05-31
Two things: 
First, that is definitely not the code requested (the code requested would be from the PHP source for obvious reasons: it is there where the bug is to be found after all).
Second, how are you sending your output to the client (the browser, i.e. firefox) ? For instance in HTML "<p>foo</p>" should work. But so should: "<p>foo<p>bar". When the rendering engine is dealing with `tag soup' combining various constructs may make it think that "<p>foo</p><p>bar" actually resolves to "<p>foo&lt;/p&gt;<p>bar". 

You may be able to fix the second issue by using a STRICT doctype and validating your page using the W3C validator (and fixing anything it complains about).

EDIT: Ah seems like Netbeans tries to be smarter than the programmer... Usually such things are a recipe for trouble when you don't know its limits.

---

### Post by masux594 on 2009-05-31
first of all, using Jaunty x64 i cannot use IE for obvious reason ;) [also for a personal hate].. However,  i don't want to "simulate" the tag, or write html code for the client side.. well, at this point, i think that netbeans think that i'm a stupid.. anyone know how to disable this feature?? Maybe that while typing i had press some "superstrange" key combinations.. that in the netbeans setting is only a checkbox to uncheck.. 

tnx to everybody!

Sysc A

P.s. Using xhtml 1.0 strict  header:-)

---

### Post by tturrisi on 2009-06-01
Post the PHP code, NOT the html code.
Open the .php file in a text editor and copy+paste the code here. (do NOT post "view source" output)

---

### Post by masux594 on 2009-06-01
Is hard to post the entire code.. using ajax i would post about 4&#8722;5 files.. but, the file that raise this kind of error is

```

/*
 * Manage and edit the menu action
 */
    include 'utils/Connect.php';
    include 'utils/SProcFunctions.php';

    If (!IsDefaultProg($_GET['prog_act'])) {
        echo '<div class="div_act">';
        switch ($_GET['prog_act']) {
            case '000152':
                    /* link semplice */
                    ?>
                        <p>Fill the form</p>
                        <table>
                            <tr>
                                <td>Go to page</td>
                                <td><input type='text' name='link_page' class='text'&#8725;></td>
                            </tr>
                        </table>
                    <?php
                break;

            case '000154':
                    /* collegamento asincrono */
                    ?>
                        <p>Fill the form</p>
                        <table>
                            <tr>
                                <td>Position</td>
                                <td>
                                    <select name='prog_position' class='select'>
                                    <?php
                                        echo DoCreateItemsTabCombo('MENU', 'POSITION', '');
                                    ?>
                                    </select>
                                </td>
                            </tr>
                            <tr>
                                <td>text</td>
                                <td>
                                    <select name='page_to_show' class='select'>
                                    <?php
                                    echo DoCreateItems(
                                        'SELECT code, des FROM '.GTDL('tab_pages', 'IT'),
                                        'code', 'des', FALSE
                                    );
                                    ?>
                                    </select>

                                </td>
                            </tr>
                        </table>
                    <?php
                break;
        }
        echo "</div>";
    }
    
    include 'utils/Disconnect.php';

```and the error raised on "<p>Fill the form</p>".. and go on with the other tags from this sentence ..Looks strange but it happens!

sysc A

---

### Post by masux594 on 2009-06-13
Well, finally i've found the solution of this mistake!! wow, after some weeks, i realized that the problem is the keyboard!! i was programming in another language, and i wasn't able to comment a row.. so i say ".. WTF is that?!".. after many trials, i understand that the "/" that is in the numpda is different form the "/" in in the "7" key.. Looks strange but, replacing  all the "/" in the source code with the "/" in the "7" key all seems to work perfectly!

P.s. Im going to resolve this strange problem with the keyboard!

Sysc A!

P.p.s. Tnx to all that dedicate some time tho my trouble!

---

