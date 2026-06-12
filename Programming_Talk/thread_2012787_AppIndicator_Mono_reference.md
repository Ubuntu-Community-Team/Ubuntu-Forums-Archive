---
title: "AppIndicator Mono reference"
date: 2012-06-29
forum: Programming Talk
---

### Post by Canha on 2012-06-29
Hello :) I want to use AppIndicator on my mono gtk# 2.0 application, which reference do I need to set/use? And I don't mean the "using AppIndicator;" instruction.

Thank you

---

### Post by directhex on 2012-06-30
Install the package [libappindicator0.1-cil-dev](apt:libappindicator0.1-cil-dev) and reference the assembly in your project by passing -pkg:appindicator-sharp-0.1 to the compiler (or ticking a reference on appindicator-sharp.dll in the MonoDevelop project references window)

See SparkleShare/Linux/SparkleStatusIcon.cs in the SparkleShare source code for sample usage.

---

### Post by Canha on 2012-06-30
Thank you. Indeed, the key to this was not having that package installed. After installing, it is as simple as it gets, you just need to Edit references and tick the box. The sample usage tip was nice as well, kudos!

---

