---
title: "could not login to remote server(Via SSH) from different country"
date: 2019-02-12
forum: New to Ubuntu
---

### Post by surabhi.5harsha on 2019-02-12
hello, 
I'm from India and I'm studying in Germany. I was using SSH remote desktop [my university server desktop] from my personal laptop in (ssh username@ip_address) manner. But, for a short period of time, I have to move to my home country. But, unfortunately, I could not even login into it. what to do to log in again. I am getting an error message like "ssh: connect to host 134.109.192.205 port 22: Connection timed out" after 5minutes. Please help me to restart my work. 
Thank You.

---

### Post by 1clue on 2019-02-12
Somewhere along the line there is a firewall blocking port 22. It could be the server you're trying to connect to, or the university's firewall, or your ISP in India, or anywhere in between.

I know that there are ways to filter firewall rules by geographical location with some degree of accuracy. It may be that your university has determined that only people in Germany (or in the EU) should be allowed to connect. Personally that's where I would look first.

---

### Post by 1clue on 2019-02-12
Thinking about it, there is also a good chance that the university blocks port 22 outside of the university network. So you'd need to connect to a VPN in order to connect using port 22. This is a common approach to security in general.

---

