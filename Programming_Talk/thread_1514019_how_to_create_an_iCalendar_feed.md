---
title: "how to create an iCalendar feed"
date: 2010-06-20
forum: Programming Talk
---

### Post by vruum on 2010-06-20
Hi all
I am working on a small webservice project, for me and my coworkers. The goal of the project is to allow a user to send a request to a server, the server then logs on to a webpage, containing the users work schedule, and return iCalendar data, thus allowing the users to sync their google calendar or phone with their work schedule. 
The problem I'm having is that the server only fetches the schedule from the day of the request and 30 days into the future, so whenever the user update his calendar, old entries are deleted. so my question is, if there is any way to tell the client to not delete old events, without persisting any data serverside, so just update/add the events actually contained in the feed?

---

