---
title: "How to start a conversation with pymsn"
date: 2009-01-27
forum: Programming Talk
---

### Post by patrick91 on 2009-01-27
Hi I'm trying to create a msn bot (just for fun) and I need to send a message to a connected user when I send to the bot: !say hello to [email]me@me.com[/email], but I don't know how to start a conversation, here is the code I use:
```
import pymsn
import pymsn.event

import os, operator, sys

class ClientEventHandler(pymsn.event.ClientEventInterface):
       def on_client_error(self, error_type, error):
        if error_type == pymsn.event.ClientErrorType.AUTHENTICATION:
            print ""
            print "********************************************************"
            print "* You bummer ! you did input a wrong username/password *"
            print "********************************************************"
        else:
            print "ERROR :", error_type, " ->", error

class Events(pymsn.event.ClientEventInterface):
    def on_client_state_changed(self, state):
        if state == pymsn.event.ClientState.CLOSED:
            self._client.quit()
        elif state == pymsn.event.ClientState.OPEN:
            self._client.profile.display_name = "patrick"
            self._client.profile.presence = pymsn.Presence.ONLINE
            self._client.profile.personal_message = "!!!"

class Conversation(pymsn.event.conversation.ConversationEventInterface):
    def __init__(self, conversation):
        self.conversation = conversation
        pymsn.event.conversation.ConversationEventInterface.__init__(self, self.conversation)

    def on_conversation_message_received(self, sender, message):
        messaggio = message.content
        
        if '!say' in messaggio:
            messaggio = messaggio.replace('!say', '').strip()
            pieces = messaggio.split()
            try:
                to = pieces[-2]
            except IndexError:
                to = 0
            if to == 'to':
                person = pieces[-1]
                message = ' '.join(pieces[0:-2])
                print 'I don\'t know how to send "%s" to %s' % (message, person)
            else:
                self.conversation.send_text_message(pymsn.ConversationMessage(messaggio))

    def on_conversation_nudge_received(self, sender):
        self.conversation.send_nudge()

    def on_conversation_user_typing(self, contact):
        print "%s inizia a scrivere" % contact.display_name
        
    def on_conversation_user_joined(self, contact):
        print contact, "e' entrato"
        
    def on_conversation_user_left(self, contact):
        print contact.account, "se n'e' andato"

class Invite(pymsn.event.InviteEventInterface):
    def on_invite_conversation(self, conversation):
        self._conversation = Conversation(conversation)

class MsnBot(pymsn.Client):
    def __init__(self, server, account, proxies={}):
        pymsn.Client.__init__(self, server, proxies)
        pymsn.Client.login(self, *account)
        self._events_handler = Events(self)
        self._invite_handler = Invite(self)

server = ('messenger.hotmail.com', 1863)
account = ('@', '')

client = MsnBot(server, account)
client_events_handler = ClientEventHandler(client)

if __name__ == "__main__":
    import gobject
    mainloop = gobject.MainLoop()
    mainloop.run()

```

thanks for any help :)

---

