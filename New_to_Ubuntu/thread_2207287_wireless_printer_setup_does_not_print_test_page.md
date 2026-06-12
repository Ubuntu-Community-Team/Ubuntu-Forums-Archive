---
title: "wireless printer setup does not print test page"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by Ralph_Lam on 2014-02-22
The printer setup looks absolutely identicle in Ubuntu, Mint, SolydX, and Manjaro.

Using the printer set up in all but Ubuntu, I am able to "see" my wireless printer and print a test page, and print anything I want from any program that has the ability to print.

When trying to set it up in Ubuntu, the steps all look the same, it finds the printer, searches for drivers, adds the printer to my printer list, and it says that it has sent a test page to the printer, but the printer never kicks into action.

Strange that Mint, being based on Ubuntu, can do it, but Ubuntu can't.

Anyway, what am I missing?

Thanks

---

### Post by r.stiltskin on 2014-02-22
Maybe a firewall problem.  You might find a clue in /var/log/cups/access_log.

---

