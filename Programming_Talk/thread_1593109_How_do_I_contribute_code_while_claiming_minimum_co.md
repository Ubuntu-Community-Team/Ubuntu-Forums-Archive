---
title: "How do I contribute code while claiming minimum copyright for my changes?"
date: 2010-10-11
forum: Programming Talk
---

### Post by Flimm on 2010-10-11
I want to contribute code to a GPLv3 licensed project in such a way as to make potential future license changes as easy as possible for the maintainers.

I would like to license my own changes as freely as possible, even more free than an MIT license if possible. I don't want to require attribution in the source code, I don't want to require that a section of my license be reproduced (unlike BSD or MIT licenses), and I especially want the copyright holders of the project to be able to change the license of the project to something else without needing to get my permission first.

I've considered including something like this in the header of every file I modify:

[FONT="Monospace"]# To the extent possible under law, David D. Lowe has waived any copyright and related or neighbouring rights to his modifications to the work found in revisions 456 of this Bazaar branch. 
# In no way are the patent or trademark rights of any person affected, nor are the rights that other persons may have in the work or in how the work is used, such as publicity or privacy rights.
# David D. Lowe makes no warranties about the work, and disclaims liability for all uses of the work, to the fullest extent permitted by applicable law.
# When using or citing the work, you should not imply endorsement by David D. Lowe.
# The past four paragraphs may be deleted.[/FONT]

Can anyone find any instances of people doing this already? Or is there no easy way to license just your changes to a project under a more permissive license?

---

### Post by aspiredfang on 2010-10-11
If you are contributing to GPL software, it would help to understand how GPL actually works.

[http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

---

### Post by Npl on 2010-10-11
if your changes are big enough you could put them under a permissive license like the BSD or MIT. If the project is GPL it must be a compatible license, something homebrewn wont help you there and just stating your interest and then say be free to delete and thus ignore them serves no point anyway.

---

### Post by juancarlospaco on 2010-10-11
use the WTFPL
:)

---

### Post by Flimm on 2010-10-11
> **aspiredfang said:**
> If you are contributing to GPL software, it would help to understand how GPL actually works.

[http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

I understand how the GPL works. I understand the difference between a license and a contract.

That's not the issue. The issue is when a project manager decides they want to change the license of a project. In order to do so, they have to contact every single contributor to the code, and get their permission. Every last one. If someone doesn't reply in time, or refuses to give permission, they have to rewrite their code.

I would like to make it clear and legally binding now that I license my changes to the code in the most permissive way possible. The resulting project would remain under the GPLv3. However, if one day the project maintainers decide they want to change the license, they wouldn't even have to bother contacting me. That's the idea, anyway.

> **Npl said:**
> if your changes are big enough you could put them under a permissive license like the BSD or MIT.
How would I do that? How do I word it to make it clear that only my changes are licensed under the MIT? Has anyone done this before?

What if my changes aren't that big? Does that mean that future project maintainers would not need to get my permission to change the license of a project?

> If the project is GPL it must be a compatible license, something homebrewn wont help you there and just stating your interest and then say be free to delete and thus ignore them serves no point anyway.
I considered using [CC0](http://wiki.creativecommons.org/CC0_FAQ), but it's incredibly long and is worded in such a way as to make it difficult to make it apply to changes only.
"Feel free to delete" would serve a point for code under revision control.

---

### Post by diesch on 2010-10-11
International copyright law isn't an easy thing and I don't think it's possible to make your statement legally binding and clear enough to make it easier for the project manager to understand it than to just try to contact you together with all the other contributors.

Just make sure you provide an email address where it's likely that you can read for the next ten years and reply in time if you get asked seems for me the best way to minimize the projects manager's work.

---

### Post by spjackson on 2010-10-11
> **Flimm said:**
> I understand how the GPL works. I understand the difference between a license and a contract.

That's not the issue. The issue is when a project manager decides they want to change the license of a project. In order to do so, they have to contact every single contributor to the code, and get their permission. Every last one. If someone doesn't reply in time, or refuses to give permission, they have to rewrite their code.

The FSF now has a method that they claim means that they don't have to go through that chore. You can assign your copyright rights to the owner of the project. This is what FSF requires in order for it to accept "legally significant" changes. [http://www.gnu.org/prep/maintain/maintain.html#Legally-Significant]("http://ubuntuforums.org/href-")

See also [http://www.gnu.org/licenses/why-assign.html](http://www.gnu.org/licenses/why-assign.html)

Other project owners have different requirements, e.g. [http://qt.nokia.com/merge_requests/agreement/](http://qt.nokia.com/merge_requests/agreement/)

> 
I would like to make it clear and legally binding now that I license my changes to the code in the most permissive way possible. The resulting project would remain under the GPLv3. However, if one day the project maintainers decide they want to change the license, they wouldn't even have to bother contacting me. That's the idea, anyway.


How would I do that? How do I word it to make it clear that only my changes are licensed under the MIT? Has anyone done this before?

What if my changes aren't that big? Does that mean that future project maintainers would not need to get my permission to change the license of a project?
For any particular project, I suggest that you follow the requirements for that project. I don't see how you can practically do any more than that.

If, in a particular case copyright ownership becomes fragmented (as in the circumstance you describe) then that is down to the project maintainers, and there is not much you as an individual contributor can do to stop that, even if you try to do your best in your own corner of the project.

---

### Post by nvteighen on 2010-10-12
The thing is your creating a derivate work of a GPLv3 project. So, stick to the GPLv3. You can't change the license, otherwise the purpose of the GPLv3 would be defeated: your "license" would make it possible to reuse your code in propietary code, for instance.

So, read the project's contribution requirements: if they ask you to assign copyright to the development team, that means that the decisions about copyright will be taken collectively by the rules that team has set to take such decisions... Of course, if you don't like their requirements and procedures, you can create a fork of the project (the thing is: do that only if your changes are really significant, the mantainers are doing things wrong and you've told them).

If there aren't any contribution requirements, contact the mantainer to tell him you want to assign copyright to him or the team. That'd be surely the cleanest way to do it.

---

### Post by TheBuzzSaw on 2010-10-12
Just hand the copyright itself over to the project managers. Beyond proper credit, what else do you want?

---

### Post by Flimm on 2010-10-14
> **nvteighen said:**
> The thing is your creating a derivate work of a GPLv3 project. So, stick to the GPLv3. You can't change the license, otherwise the purpose of the GPLv3 would be defeated: your "license" would make it possible to reuse your code in propietary code, for instance.I see your point. Even just my changes would count as derivative work. I didn't think of it that way. I guess I'll have to give up this idea then.

> **TheBuzzSaw said:**
> Just hand the copyright itself over to the project managers. Beyond proper credit, what else do you want?I don't even want proper credit. How easy is it to hand the copyright over? I wouldn't want to have to sign a physical piece of paper, like you do for the FSF.

---

