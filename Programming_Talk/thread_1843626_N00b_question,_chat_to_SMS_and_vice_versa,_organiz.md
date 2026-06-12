---
title: "N00b question, chat to SMS and vice versa, organizing messages, need help with detail"
date: 2011-09-13
forum: Programming Talk
---

### Post by Virgil0211 on 2011-09-13
I'm still at a beginner's level when it comes to programming (in Python, no less), but I thought it wouldn't hurt to post this question to see if there was any help that could be offered or if someone had already written a program that did this.

(Names and locations redacted for privacy reasons)

I'm currently working with my friend for a three-day event that's coming up. It's a non-profit event with a rather specialized focus, but it tends to pull in significant attendees. The staff is composed almost entirely of volunteers, and there is minimal budget for equipment beyond what staff members are able to bring to the table. I've volunteered at such events myself for a while, and one constant problem has been the flow of information. It's not unusual for problems to arise because some staff heads don't have the requisite information, or because volunteers are unable to find their superiors in order to consult them on decisions. We do have walkie talkies for staff members, but nowhere near the required budget to distribute these to all volunteers. 

As such, my friend and I came up with the idea of using twitter and AIM. The idea was that, as Twitter and AIM could send text messages, that this would make it possible to disseminate information to anyone who had a cell phone. Until recently, I'd been trying to determine if there was a way to expand this further into something that was, effectively, an SMS-based alternative to walkie talkies that utilized free programs. Ideally, I'd like to make it so that lieutenants (those who manage groups of volunteers) and those underneath them could communicate back and forth easily without directly exchanging cell phone numbers. In addition, I'd like to make it so that department heads and lieutenants could send queries to the computer for information (the time of such an event, what event is scheduled to occur in which room, what volunteers are currently on duty, etc). 

As far as I can tell, I need to set up a program that would be something of a combination between an employee management program as well as a chat program. I guess I'll just go into what I feel I need to ask now.

1. Have any open-source programs been developed that sound similar to this?

2. What areas of programming do I need to focus on in order to make this work?

3. Does this look like something that would require a server, or should a desktop computer be capable of doing this?

4. Is this a stupid idea? (Am I barking up the wrong tree, biting off more than I can chew, etc...) 

I feel a bit worried that I haven't quite described everything I need to, so let me know if I need to clarify anything further. When I typed 'open-source python chat program' into google, I got a few sites where questions about chat programs such as this were met with a bit a flaming, so I hope I'm not coming off as ignorant (though I probably am. :-P). 

Thank you for reading the above wall of text, for your time, and any advice you may be able to render.

Have a pleasant day.

---

### Post by Jacks0n on 2011-09-16
In terms of creating a custom solution, you're not only looking at programming itself, but sitting down and designing the program architecture, designing the UI, supporting multiple platforms (multiple phone OS's), etc. It'll probably be a lot of work.

For the real time communication my suggestion would be to setup an IRC (chat) server. Basically every smart phone has clients available, and if not you can install one of the many web-clients. You can setup permissions, where some people can moderate, others can't speak, etc. It's freely available, you don't pay per message, and you can easily moderate the users.

If you're not looking for a massive group server, maybe try Google Talk/Jabber for smaller groups of people to talk in real time.

And then on top of that maybe you could setup a wiki, to host commonly known information so people can refer to that to organize things. Once you have a chat, put the information in the wiki so it's all organized. You can easily password protect both technologies also, and they're freely available.

I've done this before at a conference before, where we used IRC and a wiki. It was very helpful. Hope that helps!

---

### Post by Virgil0211 on 2011-09-16
> **Jacks0n said:**
> In terms of creating a custom solution, you're not only looking at programming itself, but sitting down and designing the program architecture, designing the UI, supporting multiple platforms (multiple phone OS's), etc. It'll probably be a lot of work.

For the real time communication my suggestion would be to setup an IRC (chat) server. Basically every smart phone has clients available, and if not you can install one of the many web-clients. You can setup permissions, where some people can moderate, others can't speak, etc. It's freely available, you don't pay per message, and you can easily moderate the users.

If you're not looking for a massive group server, maybe try Google Talk/Jabber for smaller groups of people to talk in real time.

And then on top of that maybe you could setup a wiki, to host commonly known information so people can refer to that to organize things. Once you have a chat, put the information in the wiki so it's all organized. You can easily password protect both technologies also, and they're freely available.

I've done this before at a conference before, where we used IRC and a wiki. It was very helpful. Hope that helps!

Thank you. That is a great help, and I've already suggested the wiki idea. The main thing that I'm concerned about, however, is the ability to use SMS/text messaging so that those without smartphones could make use of the system. We're staffed primarily with volunteers, many of whom do not have smartphones. I was hoping to develop a system where people could text a single number, which would direct to a computer, which could then copy and paste the message to others within a specific group. Say, for example, lieutenant A in group A wanted to message all of the volunteers in group A. I'd want him to be able to send a text message that the computer would receive, check which group the sender belongs to, and then re-send it to the other members of that group. I could theoretically do it manually by keeping open a database file that lists all group members, checking the sender against that, and then copy/pasting the message into other AIM chat windows, so I think a program could theoretically be developed to accomplish this. There are a few other things I'd like to implement as well if I can manage it in time, such as being able to send a query message that would allow someone to check the database for info, such as who is listed as being on-duty in their group at the time, without sending it to the rest of their group, or possibly being able to send messages to other groups (such as department heads and higher-ups) without sending that message to the rest of their group. 

Another advantage of this is that we could take down the cell phone numbers of volunteers without having to directly give them out to other individual employees and sign an agreement not to give out this personal information as well as delete it once the convention concludes. I think this could possibly help as people concerned about protecting their privacy wouldn't have to give out their number to someone they've just met. 

I'm sorry if I'm coming off as sounding a bit n00bish. The idea for this project is a big part of what inspired me to attempt programming in the first place. I've learned alot on the way here (at least, it feels like alot to me), so I'll definitely have gained something out of it even if it doesn't work out as planned. However, I still want to do whatever I can to get this project done, or at least cobble together pieces from other open-source software that would get the job done. 

I guess one of the things I'm asking is how networks like AIM send SMS/text messages from a computer to a phone and back, and whether or not this could be implemented in other chat programs. I'd like to be able to have this running for a period of 3.5-4 days without interruption, and to be able to manually interface with the system to send messages to individuals, groups, or all contacts from the computer (which, ideally, would be kept in the Operations room). With these requirements, would it be something I would have to use a local server for? If so, could I convert a first model Playstation 3 for this purpose (I ask because, if I require a server, that would be about the only option available to me). 

Again, thank you for your reply. It's been a great help. I apologize if it feels like I'm rambling a bit. I have difficulty structuring my off-the-cuff comments. :-P

---

