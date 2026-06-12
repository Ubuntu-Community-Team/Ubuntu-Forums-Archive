---
title: "Positioning of @media within a css style sheet - method to madness?"
date: 2015-10-31
forum: Programming Talk
---

### Post by Ace..... on 2015-10-31
As a newcomer to responsive css, I downloaded a template.
It had some display errors, and seemed to behave in an illogical manner, but.....
.... I overcame those issues, and created a web page that would display correctly at all appropriate resolutions.

However; to me, the style sheet was a mess.
Various elements/classes & resolution commands, were not in order.

Thinking of the future; and not wanting to have to re-learn everything, I set about tidying, and commenting the relevant elements (and commenting out unused code).

Major division sections were placed in correct order, along with sub divisions, and <h> & <p> etc.
I then moved all the @media(max-width:XXXXpx) into a descending order, starting at 1440px down to 320px.

I had assumed that, like js commands, these @media groupings could be placed anywhere, but would be acted upon according to pixel resolution.
(placing them in logical order would then simplify future re-coding).

Apparently not.
After reloading the web page, many of the original display errors have returned.

It's not a disaster....... I can work my way through the changes required for each resolution.

So..... leaving aside the original template errors ([[COLOR=#0000cd]one of which is outlined here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2301128&p=13382532#post13382532")).....
... am I right in having all the resolution changes grouped together in descending order?

OR was there method to the apparent madness of having @media(max-width:XXXXpx) groupings out of sequence?

---

### Post by Ace..... on 2015-11-01
Having completed the tidying of the code, in the now ordered descending resolution groupings....
.... I can't see any good from having resolution groups out of order.

It created confusion, and errors, even in the original example website display.

I woke up this morning, and the first thought in my head was 'cascading style sheets' and what it meant.
Sometimes one can't see the wood for the trees. :)

However I am glad of the errors, as they have forced me to get a grip of the code, and gain the understanding that I needed.

I guess, where classes are specific to a single page, the resolution changes could be kept together within page sections of the stylesheet.
But it seems too risky.
I'd rather have all changes per resolution together, and add comments to indicate which pages are being referred to.

It does cause it bit more switching up and down the style sheet, but using 'Find' makes this a minor inconvenience.
:)

---

### Post by Dimarchi on 2015-11-02
Allow me to introduce you to the concept of specificity in the context of CSS:

[URL="https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity"]https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity
[/URL]
That page should give you some more insight into what you have discovered on your own.

---

### Post by Ace..... on 2015-11-03
> **Dimarchi said:**
> Allow me to introduce you to the concept of specificity in the context of CSS:

[URL="https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity"]https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity
[/URL]
That page should give you some more insight into what you have discovered on your own.

Thank you for that link; it was extremely useful, and very clearly written.

:)

---

