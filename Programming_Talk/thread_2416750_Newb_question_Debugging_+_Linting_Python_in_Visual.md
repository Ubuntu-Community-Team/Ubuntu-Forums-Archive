---
title: "Newb question: Debugging + Linting Python in Visual Studio Code"
date: 2019-04-14
forum: Programming Talk
---

### Post by Drone4four on 2019-04-14
I’m closely following along Microsoft’s official docs for VSC for [Python debugging](https://code.visualstudio.com/docs/python/debugging) and [linting](https://code.visualstudio.com/docs/python/linting). 

The Linting guide explain this in the introductory paragraphs:

> By default, linting for Python is enabled in Visual Studio Code using [Pylint](https://www.pylint.org/), and you can enable other linters of your choice. You can easily enable and disable all linting by using the **Python: Enable Linting** command. To enable linters other than the default PyLint, open the Command Palette (**Ctrl+Shift+P**) and select the Python: Select Linter command. This command adds `"python.linting<linter>Enabled": true` to your settings, where `<linter>` is the name of the chosen linter. See Specific linters for details.

When I navigate to Pylint.org (the hyperlink in the first sentence there), I install the Linter as it instructs for my Linux distro (Manjaro). I restart VSC. Then when I invoke Ctrl+Shift+P and enter ‘python’ or ‘pylint’, nothing turns up. It’s as if it doesn’t exist on my system even though I clearly just installed it. 

What am I missing here? How do I install the Python Linter as explained in the official tutorial there?

I’m looking for a solution that is probably trivial and obvious to the expert programmer. I’m ready to be gently hit over the head with a “cluebat.”

By the way: What happened to this sub-forum's thread history? It looks like it only goes back 4 weeks. Did the moderators wipe out years worth of previous posts?

---

