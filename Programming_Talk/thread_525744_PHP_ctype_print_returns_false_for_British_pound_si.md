---
title: "PHP ctype_print returns false for British pound sign"
date: 2007-08-14
forum: Programming Talk
---

### Post by GurneyHalleck on 2007-08-14
I'm having no luck whatsoever in getting to the bottom of this.

In a script that I've used for months without problem on shared hosting space, the following appears:

$price = '£3.04';
$valid = ctype_print($price);

This returns true on my web host's Linux server, so long as I specify the locale like so:

setlocale(LC_CTYPE, 'en_GB', 'en', 'en_GB.utf8', 'en_GB.UTF-8');

However, no matter what I've tried, I cannot get the ctype_print to return true for the British pound sign under Ubuntu 7.04.

I've tried reinstalling the locale packages, reconfiguring them, setting environment variables. Nothing permits ctype_print to consider the British pound sign to be a printable character.

Does anyone know how to fix this? It's causing a problem because it brings my script to a halt. (My script assumes that non-printable characters are a sign of dangerous data.)

---

### Post by GurneyHalleck on 2007-08-24
Has no one else encountered this?

---

