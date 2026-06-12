---
title: "problem running system command from rb script"
date: 2007-04-28
forum: Programming Talk
---

### Post by kitmobley on 2007-04-28
i'm having problems getting this to run from the web. I've already added www-data to the usergroup "users" and can't seem to get it work. works from if i do it manually so i don't think there's anything wrong with jabber. anyone have any ideas? please help!

#!/usr/bin/env ruby

require 'cgi'

cgi = CGI.new('html4')

username = cgi['username']
passwd = cgi['passwd']
#fname = cgi['fname']
#lname = cgi['lname']
#gloid = cgi['gloid']
result = 0

# Add User to Jabber Server
ENV['HOME'] = '/home/kit'
system('sudo /opt/ejabberd-1.1.1/bin/ejabberdctl register ' + username + ' talk.macgames-network.com ' + passwd + ' > /dev/null')
result = $?.to_i

# Result codes
# 0     All is cool
# 256   User already exists in server
# 512   Invalid user parameters

rstatus = 500
rmessage = 'Unknown error.'

case result
when 0
        rstatus = 201
        rmessage = 'Account created.'
when 256
        rmessage = 'User already exists.'
when 512
        rmessage = 'Invalid values in parameters.'
end

cgi.out('status' => rstatus.to_s) {
        rmessage

}

keeps kicking me back User already exists

wtf
am i missing something with the server?

here's the ls -l results for the file

-rwxrwxrwx 1 root root          747 2007-04-28 17:08 adduser.rb

---

