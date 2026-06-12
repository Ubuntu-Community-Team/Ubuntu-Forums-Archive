---
title: "firefox/mozilla focus on popup bug ?"
date: 2006-04-21
forum: Programming Talk
---

### Post by lafleche on 2006-04-21
Hello,

this is a copy of a post from comp.lang.javscript hoping you guys are more reactive.

So I'm trying to get a popup to keep focus when it is re-clicked.
The script below is supposed to produce this exact behaviour,
however it doesn't work, at least on firefox 1.0.7 and moz 1.7.12
(linux kubuntu). It does work with konqueror.
It seems to work with firefox on windows but not with IE (not completly
sure though).

<script type="text/javascript">
var WindowObjectReference = null; // global variable

function openFFPromotionPopup()
{
  if(WindowObjectReference == null || WindowObjectReference.closed)
  /* if the pointer to the window object in memory does not exist
     or if such pointer exists but the window was closed */

  {
    WindowObjectReference =
window.open("http://www.spreadfirefox.com/",
           "PromoteFirefoxWindowName",
"resizable=yes,scrollbars=yes,status=yes");
    /* then create it. The new window will be created and
       will be brought on top of any other window. */
  }
  else
  {
    WindowObjectReference.focus();
    /* else the window reference must exist and the window
       is not closed; therefore, we can bring it back on top of any
other
       window with the focus() method. There would be no need to
re-create
       the window or to reload the referenced resource. */
  };
}

</script>

(...)

<p><a href="http://www.spreadfirefox.com/"
target="PromoteFirefoxWindowName"
onclick="openFFPromotionPopup(); return false;"
title="This link will create a new window or will re-use
an already opened one">Promote Firefox adoption</a></p>

The weird thing is... it is copied from
[http://developer.mozilla.org/en/docs/window.open#Examples](http://developer.mozilla.org/en/docs/window.open#Examples) !

I must mention that i've activated javscript and allowed it to control
focus with firefox and even disabled bpopup blocking, but it didn't
helped :(, neither did the many variante i've found on the web or in
this newsgroup.

I'm really clueless, but i'm just catching up with javascript so i hope
i've missed an obvious point.

So if anyone

---

