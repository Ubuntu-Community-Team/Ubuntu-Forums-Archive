---
title: "BBCode question."
date: 2010-02-18
forum: Programming Talk
---

### Post by Krupski on 2010-02-18
Hi all... I think this counts as "programming", so I'll ask. Apologies to the mods if it's not supposed to be here.

Anyway, I'm running a temporary message board using PHPBB3 and I made a BBCODE to allow creating a button on the screen which will open a link in a new window.

I would appreciate it if any PHPBB3 BBcode guru could look at it and tell me if there are any fundamental mistakes. It does work, but did I do it right???

BBCode Usage
```

[link]{URL},{TEXT}[/link]

```

HTML Replacement
```

<button
type="button"
title="{URL}"
onMouseOver="window.status='This button opens {URL}'; return true"
onMouseOut="window.status=''; return true"
onClick="window.open('{URL}', '_blank')" />
&nbsp;&nbsp;
{TEXT}
&nbsp;&nbsp;
</button />

```

Help line
```

Add a link BUTTON: [Link]URL, Button Text[/Link]

```

What I'm concerned about is something to do with "not using {TEXT} in HTML tage but using {SIMPLETEXT} instead for security reasons".

But, "SIMPLETEXT" (and the other recommended one... "IDENTIFIER" do not work if the parameter is blank (i.e. a button with no label)).

That is, **(LINK)[www.ubuntu.com](www.ubuntu.com), Please click for Ubuntu(/LINK)** works, but **(LINK)[www.ubuntu.com,(/LINK](www.ubuntu.com,(/LINK))** fails (unless {TEXT} is used).

By the way, the above example uses parentheses instead of brackets to avoid messing things up. 

Lastly... why don't I ask on a PHPBB3 forum? Because they all answer as if the person is an expert. An answer that flies over my head is no answer.

At least here I know I'll get REAL help.

Thanks all!

-- Roger

---

