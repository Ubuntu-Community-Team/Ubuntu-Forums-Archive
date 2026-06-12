---
title: "HOWTO: Using Indic fonts in Kubuntu7.10 (Gutsy)/ openoffice"
date: 2008-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by ddrake on 2008-01-18
Hello

 I recently helped out my friend in using Indic fonts in openoffice2.3 on
Kubuntu7.10 (Gutsy). And I made a brief guide which I think might be
useful to others. Feedback most welcome.

  Here it goes:
[B]
Enabling the keyboard for Indic fonts - specifically telugu fonts on Kubuntu 7.10 (Gutsy)[/B]
======================
You can use either adept manager or use the apt-get commands to install the
following packages:
 A: language-pack-te language-pack-kn language-pack-hi language-pack-kde-te language-pack-kde-kn language-pack-kde-hi 
 B:  ttf-telugu-fonts ttf-kannada-fonts ttf-devanagari-fonts
 C: openoffice.org-l10-ta-in,  openenoffice.org-l10-te-in, openenoffice.org-l10-hi-in

Next go into KDE Control Center (or in the Kubuntu it is: K->System Settings)
A.1; Choose 'Regional & Language'
A.2: Choose  'Keyboard Layout' and in the 'Layout' Tab, Click to 'Enable Keyboard Options'.
A3:  Next, under available keyboard, choose the India (see indian flag) option
     Next under keyboard model choose 'Generic 105(Intl)PC' from the dropdown menu.
     Next in 'Active Layouts' click the 'add' button. This will result in a new line try coming up  ' India' under 'layout' column and 'in' under 'keymap' column. 
     Next click on that new line to select it. After selecting it, choose the
      'layout variant' - in the drop down menu, we get several languages. Choose
        one of them and then edit the label - giving your own tri-letter acronym.
     Next press enter for these options to be reflected back into the 'Active layouts' box.
     You can choose several languages under the indic languages, adding the 'india' available
     layout to the 'active layouts' box and choosing a different variant.
A4. Choose the next top-level tab 'Switching Options' and click enable the 'Show country Flag'.
    Next choose the 'Switching Policy' to be at the window level (enable the button).
A5 Choose the next top-level tab 'Xkb options'.And in it, click enable the 'Enable Xkb options'
   This will result in an enabled 'Xkb Options' box. In it click enable the entire set of
   'Group Shift/Lock Behaviour'.
A6:  Finally do click on the 'APPLY' button to the bottom right to enable all this.

This results in a country flag appearing in the task bar indicating the language keyboard enabled.

Next, choose an application - either kate or openoffice writer.

Click on the country flag on the taskbar - you get the indian flag with the language label
on it  - TEL or KAN or DEV or TAM (whatever you have choosen for Telugu or kannada or Devanagari or Tamil).

Start typing and you get the appropriate language characters.

 

 You can also look up:> [http://www.swecha.org/wiki/Input](http://www.swecha.org/wiki/Input) to get the instructions for 
the above as well as the keyboard layout used in the INSCRIPT KEYMAP. 
 You can download the keyboard layout available as a pdf file > ([http://tdil.mit.gov.in/isciichart.pdf](http://tdil.mit.gov.in/isciichart.pdf)).
In addition, this website has interesting information:> 
[http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts](http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts)



---

