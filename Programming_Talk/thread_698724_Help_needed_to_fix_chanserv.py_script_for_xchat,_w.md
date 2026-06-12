---
title: "Help needed to fix chanserv.py script for xchat, whilst using bip"
date: 2008-02-16
forum: Programming Talk
---

### Post by PriceChild on 2008-02-16
Hey there, so I'm an ubuntu operator who has recently been lucky enough to find himself somewhere to keep a persistent session. After looking at the options, I settled on bip, mostly because of the way it sends you the backlog.

I connect to bip using xchat, and in xchat I use the following script, named chanserv.py:
```

# Simple chanserv helper script for Xchat
# (c) 2006,2007 Dennis Kaarsemaker
#
# Latest version can be found on http://www.kaarsemaker.net/software/
# 
# This script is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# version 3, as published by the Free Software Foundation.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

#
# Usage instructions:
# Place in ~/.xchat2 for it to be autoloaded
#
# It adds one command to xchat: /cs
# /cs understands the following arguments
# o  or op      - Let chanserv op you/others (/cs op, /cs op somenick)
# v  or voice   - Let chanserv give you/others voice
# d  or deop    - Let chanserv deop you/others (/cs deop, /cs deop somenick)
# dv or devoice - Let chanserv decoice you/others (/cs devoice, /cs devoice somenick)
# k  or kick    - Op, kick, deop (/cs kick somenick [comment])
# b  or ban     - Op, ban, deop (/cs ban somenick)
# f  or forward - Ban a user with a forward (/cs forward nick chan)
# n  or nameban - GECOS ban (/cs nameban nick)
# m  or mute    - Op, mute, deop (/cs mute somenick)
# kb or kickban - Op, kickban, deop (/cs kb somenick [comment])
# kf or kickforward - Same as kb, but with a forward (/cs kf somenick channel [comment])
# kn or kicknameban - Same as kb, but with a GECOS ban (/cs kn somenick [comment])
# l  or lart    - A combination of kick, ban, nameban, ident ban and nick ban.
# u  or unban   - Op, unban, deop (/cs u somenick)
# t  or topic   - Op, set topic, deop (/cs t New topic here)
# m  or mode    - Op, change channel mode, deop (/cs mode modes here)
# i  or invite  - With nick as argument: op, invite, deop. Without nick: invite to a channel
# bans          - Show bans that apply to someone without removing them (/cs bans nick_or_mask)
#
# * For (kick)ban and mute, it will use the ip-address or hostname instead of
#   the nickname, unless you give a complete mask as argument. This works even
#   after a person left by using /whowas. /whowas generally works up to a few
#   hours after someone left.
#
# * Unban will remove all bans matching the nick or mask you give as argument
#   (*  and ? wildcards work)
# * It won't actually kick, but use the /remove command
# * Script is made to work on Freenode, may need changes to work on other 
#   networks
# * The -n argument before any of the commands (eg: /cs -n m foo) will make you
#   stay opped after the act
#
# Apart from the /cs command it also adds automatic rejoining magic. When you
# are /remove'd from a channel, it will automatically rejoin (X-chat already can
# do that for you if kicked). When attempting to (re)join a channel which is
# invite-only, has a key set or where you are banned, the script will poke
# chanserv to let you in and will automatically let you in if ChanServ helps
#
# Changelog of latest versions
# 1.0:   - Use xchat.get_info for getting the xchat dir
#        - If a nick in /cs u starts with 2 asterisks, a non-looked up nameban
#          removal will be tried. This was the last item in the todo, so this is
#          1.0
# 1.0.1: - Add voice/devoice
# 1.0.2: - Fix complete mask detection
#        - Fixed downloader
# 1.0.3  - Added /cs bans -- determine which bans apply to someone without removing them
# 1.0.4  - Update download link and allow a comment in /cs lart
# 1.0.5  - Don't require a comment in /cs lart

__module_name__        = "chanserv"
__module_version__     = "1.0.5"
__module_description__ = "Chanserv helper"

import xchat
import time
import re

# Event queue
pending = []
# /whois cache
users = {}
# /mode =bd 'cache'
bans = {}
_bans = {}
# channel modes
modes = {}

intercept_akick = False

KICK, BAN, MUTE, KICKBAN, UNBAN, TOPIC, MODE, NAMEBAN, KICKNAMEBAN, LART, INVITE, BANS = range(12)

# Main /cs command
def cs(word, word_eol, userdata):
    chan = xchat.get_info('channel')
    me   = xchat.get_info('nick')
    ctx  = xchat.get_context()
    deop = True

    if len(word) == 1:
        return xchat.EAT_ALL

    if word[1] == '-n':
        deop = False
        word.remove('-n')
        for w in word_eol:
            if w.strip().startswith('-n'):
                word_eol.remove(w)
                break

    comm = word[1].lower()

    if comm in ['o','op']:
        word_eol.append('')
        if me in word_eol[2] or word_eol[2] == '':
            for p in pending:
                if p.channel == chan:
                    p.deop = False
        xchat.command('chanserv OP %s %s' % (chan, word_eol[2]))
        return xchat.EAT_ALL

    if comm in ['d','deop']:
        if len(word) < 3: word.append(me)
        if me in word[2:]:
            for p in pending:
                if p.channel == chan:
                    p.deop = True
        xchat.command('chanserv OP %s %s' % (chan, ' '.join(map(lambda x: '-'+x, word[2:]))))
        return xchat.EAT_ALL

    if comm in ['v','voice']:
        word_eol.append('')
        xchat.command('chanserv VOICE %s %s' % (chan, word_eol[2]))
        return xchat.EAT_ALL

    if comm in ['dv','devoice']:
        if len(word) < 3: word.append(me)
        xchat.command('chanserv VOICE %s %s' % (chan, ' '.join(map(lambda x: '-'+x, word[2:]))))
        return xchat.EAT_ALL

    if comm in ['k','kick']:
        if len(word) < 3: return xchat.EAT_ALL
        if len(word) < 4: word_eol.append('')
        if word[2].lower() not in [x.nick.lower() for x in ctx.get_list('users')]:
            xchat.emit_print("Server Error", "%s is not in %s" % (word[2],ctx.get_info('channel')))
            return xchat.EAT_ALL
        schedule(Action(ctx, KICK, word[2], word_eol[3]), deop)
        return xchat.EAT_ALL
    
    if comm in ['b','ban']:
        if len(word) < 3: return xchat.EAT_ALL
        schedule(Action(ctx, BAN, word[2]), deop)
        return xchat.EAT_ALL

    if comm in ['n','nameban']:
        if len(word) < 3: return xchat.EAT_ALL
        schedule(Action(ctx, NAMEBAN, word[2]), deop)
        return xchat.EAT_ALL

    if comm in ['f','forward']:
        if len(word) < 4: return xchat.EAT_ALL
        if word[3][0] != '#':
            xchat.emit_print("Server Error", "You can only forward to a channel");
            return xchat.EAT_ALL
        schedule(Action(ctx, BAN, word[2], forward_channel=word[3]), deop)
        return xchat.EAT_ALL
    
    if comm in ['m','mute']:
        if len(word) < 3: return xchat.EAT_ALL
        if word[2][0] not in "+-=":
            schedule(Action(ctx, MUTE, word[2]), deop)
            return xchat.EAT_ALL

    if comm in ['kb','kickban']:
        if len(word) < 3: return xchat.EAT_ALL
        if len(word) < 4: word_eol.append('')
        schedule(Action(ctx, KICKBAN, word[2], word_eol[3]), deop)
        return xchat.EAT_ALL

    if comm in ['kn','kicknameban']:
        if len(word) < 3: return xchat.EAT_ALL
        if len(word) < 4: word_eol.append('')
        schedule(Action(ctx, KICKNAMEBAN, word[2], word_eol[3]), deop)
        return xchat.EAT_ALL

    if comm in ['kf','kickforward']:
        if len(word) < 4: return xchat.EAT_ALL
        if word[3][0] != '#':
            xchat.emit_print("Server Error", "You can only forward to a channel");
            return xchat.EAT_ALL
        if len(word) < 5: word_eol.append('')
        schedule(Action(ctx, KICKBAN, word[2], word_eol[4], word[3]), deop)
        return xchat.EAT_ALL
        
    if comm in ['u','unban']:
        if len(word) < 3: return xchat.EAT_ALL
        if word[2].startswith('**'):
            schedule(Action(ctx, UNBAN, word_eol[2]), deop)
        else:
            schedule(Action(ctx, UNBAN, word[2]), deop)
        return xchat.EAT_ALL

    if comm in ['l','lart']:
        if len(word) < 3: return xchat.EAT_ALL
        if len(word_eol) < 4: word_eol.append('')
        schedule(Action(ctx, LART, word[2], word_eol[3]), deop)
        return xchat.EAT_ALL

    if comm in ['t','topic']:
        if len(word) < 3: return xchat.EAT_ALL
        schedule(Action(ctx, TOPIC, word_eol[2]), deop)
        return xchat.EAT_ALL

    if comm in ['m','mode']:
        if len(word) < 3: return xchat.EAT_ALL
        schedule(Action(ctx, MODE, word_eol[2]), deop)
        return xchat.EAT_ALL

    if comm in ['i','invite']:
        if len(word) < 3: return xchat.EAT_ALL
        if word[2][0] == '#':
            xchat.command('chanserv INVITE %s' % (word[2]))
        else:
            if word[2].lower() in [x.nick.lower() for x in ctx.get_list('users')]:
                xchat.emit_print("Server Error", "%s is already in %s" % (word[2],ctx.get_info('channel')))
                return xchat.EAT_ALL
            schedule(Action(ctx, INVITE, word_eol[2]), deop)
        return xchat.EAT_ALL

    if comm == 'bans':
        if len(word) < 3: word.append(me)
        schedule(Action( ctx, BANS, word[2]), deop)
        return xchat.EAT_ALL

    if comm in ['update']:
        import thread
        thread.start_new_thread(download,tuple([]))
        return xchat.EAT_ALL
    
    # /cs is an alias for chanserv too, so don't eat anything if we're not able
    # to fulfill the request
    return xchat.EAT_NONE
xchat.hook_command('cs',cs,"For help with /cs, please read the comments in the script")

# Action class, quite powerful and extendable
class Action:
    def __init__(self, ctx, typ, arg, comment='', forward_channel=''):
        self.ctx = ctx
        self.typ = typ
        self.arg = arg
        self.nick = arg.lower()
        self.comment = comment
        self.forward_channel = forward_channel
        self.completemask = False
        self.realname = ''
        self.mask = None
        if typ in [MUTE, BAN, KICKBAN, UNBAN, BANS]:
            if self.nick.startswith('**'):
                self.realname = self.nick[2:]
                self.nick = ''
                self.mask = ('','')
            if '!' in self.nick and '@' in self.nick and self.nick.find('!') < self.nick.find('@'):
                self.nick, self.mask = self.nick.split('!',1)
                self.completemask = True
                if '@' in self.mask:
                    self.mask = list(self.mask.split('@',1))
            
        self.channel = ctx.get_info('channel')
        self.stamp = time.time()
        
    def run(self):
        # Now perform actions
        if self.typ == TOPIC:
            self.ctx.command("TOPIC %s" % self.arg)
            
        if self.typ == MODE:
            self.ctx.command("MODE %s %s" % (self.channel, self.arg))

        if self.typ == INVITE:
            self.ctx.command("INVITE %s" % (self.arg))
            
        if self.typ == UNBAN:
            for b in bans[self.channel]:
                if self.match(b):
                    if '!' in b and '@' in b:
                        self.ctx.command("MODE %s -b %s" % (self.channel, b))
                    else:
                        self.ctx.command("MODE %s -d :%s" % (self.channel, b))

        if self.typ == BANS:
            xchat.emit_print('Server Text', "Bans matching %s!%s@%s (%s)" % (self.nick, self.mask[0], self.mask[1], self.realname))
            for b in bans[self.channel]:
                if self.match(b):
                    xchat.emit_print('Server Text', b)
                    
        if self.typ in [KICK, KICKBAN, KICKNAMEBAN, LART]:
            self.ctx.command("REMOVE %s %s :%s" % (self.channel, self.nick, self.comment))
            
        if self.typ in [BAN, KICKBAN, MUTE, LART]:
            mode = 'b'
            if self.forward_channel:
                self.mask[1] += '!' + self.forward_channel
            if self.typ == MUTE:
                mode = 'q'
            if self.completemask:
                self.ctx.command("MODE %s +%s %s!%s@%s" % (self.channel, mode, self.nick, self.mask[0], self.mask[1]))
            else:
                self.ctx.command("MODE %s +%s *!*@%s" % (self.channel, mode, self.mask[1]))

        if self.typ in [NAMEBAN, KICKNAMEBAN, LART]:
            self.ctx.command("MODE %s +d %s" % (self.channel, self.realname.replace(' ','?')))

        if self.typ == LART:
            # Still todo: ident ban and nick ban
            self.ctx.command("MODE %s +b %s!*@*" % (self.channel, self.nick))
            self.ctx.command("MODE %s +b *!%s@*" % (self.channel, self.mask[0]))

    def match(self, ban):
        if '!' in ban and '@' in ban: # Not 100% reliable but it'll do
            try:
                nick, host =  ban.split('!')[:2] # Trim !#foo channel forward 
                ident, host = host.split('@')
            except:
                # If this happens, the ban is invalid and we should remove it anyway
                return True
            if nick[0] == '%':
                nick = nick[1:]
            for mtch, me in [(nick, self.nick), (ident, self.mask[0]), (host, self.mask[1])]:
                mtch = '^%s$' % re.escape(mtch).replace(r'\*','.*').replace(r'\?','.')
                if not re.match(mtch,me,re.I):
                    return False
            return True
        mtch = '^%s$' % re.escape(ban).replace(r'\*','.*').replace(r'\?','.')
        if not re.match(mtch,self.realname,re.I):
            return False
        return True

    def n2a(self,request=False):
        if self.nick in users:
            if users[self.nick][0]:
                if users[self.nick][3] > time.time() - 10:
                    self.mask = list(users[self.nick][0:2])
                    self.realname = users[self.nick][2]
                    return
        if request:
            self.ctx.command('whois %s' % self.nick)
        self.mask = None

def schedule(event, deop):
    # Add event to the pending queue and make sure all neccessary commands are
    # issued. Don't op if not sure the nick is there
    pending.append(event)
    
    # Am I op?
    for user in event.ctx.get_list('users'):
        if user.nick == event.ctx.get_info('nick') and user.prefix == '@':
            event.am_op = True
            break
    else:
        event.am_op = False
    # Deop afterwards?
    event.deop = deop
    if event.deop:
        event.deop = not event.am_op
        for p in pending:
            if p.channel == event.channel and p.deop:
                event.deop = True
    
    # Do I know the nick
    if event.typ in (BAN, KICKBAN, MUTE, UNBAN, BANS) and not event.mask:
        event.n2a(request=True)
    if event.typ in (NAMEBAN, KICKNAMEBAN) and not event.realname:
        event.n2a(request=True)
    if event.typ == LART and (not event.mask or not event.realname):
        event.n2a(request=True)

    # Do I have all bans
    if event.typ in [UNBAN, BANS] and event.channel not in bans:
        _bans[event.channel] = []
        event.ctx.command("MODE %s =bd" % event.channel)

    # Do I have all modes
    if event.typ in [TOPIC, MODE] and event.channel not in modes:
        event.ctx.command("MODE %s" % event.channel)

    run_pending()

def run_pending(just_opped = None):
    for p in pending:
        # Timeout?
        if p.stamp < time.time() - 10:
            if p.deop and len([x for x in pending if x.channel == p.channel]) == 0:
                p.ctx.command('chanserv OP %s -%s' % (p.channel, p.ctx.get_info('nick')))
            pending.remove(p)
            continue

        if p.channel == just_opped:
            p.am_op = True
        if p.typ in (BAN, KICKBAN, MUTE, UNBAN, LART, BANS) and not p.mask:
            p.n2a()
        if p.typ in (NAMEBAN, KICKNAMEBAN, LART) and not p.realname:
            p.n2a()

        # Run!
        # Mode check here! TODO
        if p.typ == MODE and p.channel in modes:
            if not modes[p.channel].would_change([x for x in p.arg.split() if x]):
                pending.remove(p)
                return

        if (p.typ in (BAN, KICKBAN, MUTE) and p.mask) or \
           (p.typ in (NAMEBAN, KICKNAMEBAN) and p.realname) or \
           (p.typ in (UNBAN,BANS) and p.channel in bans and p.mask) or \
           (p.typ in (MODE, TOPIC) and p.channel in modes) or \
           (p.typ == LART and p.realname and p.mask) or \
            p.typ in (KICK,INVITE):
            if p.am_op or (p.typ == TOPIC and 't' not in modes[p.channel].modeset) or (p.typ == BANS):
                p.run()
                pending.remove(p)
                if p.typ in (UNBAN,BANS) and len([x for x in pending if x.channel == p.channel and x.typ in (UNBAN,BANS)]) == 0:
                    bans.pop(p.channel)
                if p.deop and len([x for x in pending if x.channel == p.channel]) == 0:
                    p.ctx.command('chanserv OP %s -%s' % (p.channel, p.ctx.get_info('nick')))
            else:
                p.ctx.command('chanserv OP %s %s' % (p.channel, p.ctx.get_info('nick')))
        
# Run commands after chanserv ops
def do_mode(word, word_eol, userdata):
    ctx = xchat.get_context()
    if 'chanserv!' in word[0].lower() and '+o' in word[3] and ctx.get_info('nick') in word:
        run_pending(just_opped = ctx.get_info('channel'))
xchat.hook_server('MODE', do_mode)

# Run commands after /whois returns data
def do_whois(word, word_eol, userdata):
    users[word[3].lower()] = (word[4], word[5], word_eol[7][1:], time.time())
    run_pending()
xchat.hook_server('311', do_whois)
xchat.hook_server('314', do_whois) # This actually is a /whowas reply
# Do /whowas is /whois fails
def do_missing(word, word_eol, userdata):
    for p in pending:
        if p.nick == word[3]:
            p.ctx.command('whowas %s' % word[3])
            break
xchat.hook_server('401', do_missing)
# Display an error if /whowas also fails
def do_endwas(word, word_eol, userdata):
    for p in pending:
        if p.nick == word[3]:
            xchat.emit_print("Server Error", "%s could not be found" % p.nick)
            pending.remove(p)
xchat.hook_server('406', do_endwas)

# Add ban data tot cache (reply of /mode =b)
def do_ban(word, word_eol, userdata):
    if word[3] in _bans:
        _bans[word[3]].append(word[4])
        return xchat.EAT_ALL
xchat.hook_server('367', do_ban)

# Run commands after all bans are shown
# It does mode =bd, so 2 368 have to be received before any action is taken
MARKER  = '@@@@@@' # This is invalid as ban, so is safe, the +b bans come first
MARKER2 = '!!!!!!'
def do_endban(word, word_eol, userdata):
    if word[3] in _bans:
        if MARKER in _bans[word[3]]:
            _bans[word[3]].remove(MARKER)
            bans[word[3]] = _bans[word[3]]
            del(_bans[word[3]])
            run_pending()
        else:
            _bans[word[3]].append(MARKER)
        return xchat.EAT_ALL
xchat.hook_server('368', do_endban)

# Autorejoin on /remove and /kick
xchat.command('SET -quiet irc_auto_rejoin ON')
def rejoin(word, word_eol, userdata):
    if word[0][1:word[0].find('!')] == xchat.get_info('nick') and word[3][1:].lower() == 'requested':
        xchat.command('join %s' % word[2])
xchat.hook_server('PART', rejoin)

# Try to convince chanserv to let me in
def letmein(word, word_eol, userdata):
    if   word[1] == '473': xchat.command('quote cs invite %s' % word[3])
    elif word[1] == '474': xchat.command('quote cs unban %s' % word[3])
    elif word[1] == '475': xchat.command('quote cs getkey %s' % word[3])
xchat.hook_server('473', letmein) # +i
xchat.hook_server('474', letmein) # +b
xchat.hook_server('475', letmein) # +k

def unmute(word, word_eol, userdata):
    xchat.command('cs unban %s' % xchat.get_info('nick'))
xchat.hook_server('404', unmute)

class ModeSet:
    def __init__(self, raw_modes=[], modeset={}, new=False):
        self.modeset = dict(modeset) # Always copy
        if raw_modes:
            self.merge(raw_modes)
        self.new = new
    
    def merge(self, raw_modes):
        newmodes = raw_modes[0]; args = raw_modes[1:]
        num_plusmin = newmodes.count('+') + newmodes.count('-')
        do_set = True
        if len(args) > len(newmodes) - num_plusmin or newmodes[0] not in '+-':
            xchat.emit_print('Server Error', 'Woah mitzy, be careful with your modes :)')
        else:
            for i in range(len(newmodes)):
                m = newmodes[i]
                if   m == '+': do_set = True; num_plusmin -= 1
                elif m == '-': do_set = False; num_plusmin -= 1
                elif m.isalnum():
                    if m in 'vohbdqa':
                        continue
                    argp = len(newmodes) - i - len(args) - num_plusmin
                    if argp == 0:
                        self.modeset[m] = args[0]
                        args = args[1:]
                    else:
                        if do_set:
                            self.modeset[m] = True
                        elif m in self.modeset:
                            self.modeset.pop(m)
                else:
                    xchat.emit_print('Server Error', 'Whoah mitzy, be careful with your modes :)')

    def would_change(self, raw_modes):
        # Always return true for operator/voice etc... changes
        for m in raw_modes[0]:
            if m in 'vohbdqa':
                return True
        return str(ModeSet(raw_modes, self.modeset)) != str(self)

    def __str__(self):
        return '{' + ','.join(['%s:%s' % (x, self.modeset[x]) for x in sorted(self.modeset.keys())]) + '}'

def do_mode2(word, word_eol, userdata):
    if userdata:
        ret = xchat.EAT_NONE
        c = word[3]
        if c[0] != '#':
            return
        if c not in modes:
            ret = xchat.EAT_ALL
        modes[c] = ModeSet(word[4:],new=c not in modes)
        run_pending()
        return ret
    else:
        # Let's be lazy here
        c = word[2]
        if c[0] != '#': return
        if c not in modes:
            xchat.command("MODE %s" % c)
        else:
            modes[c].merge(word[3:])
xchat.hook_server('324',do_mode2, True)
xchat.hook_server('MODE',do_mode2, False)

def do_time(word, word_eol, userdata):
    if word[3] in modes and modes[word[3]].new:
        modes[word[3]].new = False
        return xchat.EAT_ALL
xchat.hook_server('329',do_time, True)

def joincb(word, word_eol, userdata):
    modes[word[1]] = ModeSet()
xchat.hook_command('join', joincb, priority=xchat.PRI_HIGHEST)

# Did chanserv let me in? - This function is now misnamed as it's used for akick as well
def join(word, word_eol, userdata):
    global intercept_akick
    if word[0] == ':ChanServ!ChanServ@services.':
        if word[1] == 'INVITE':                xchat.command('JOIN %s' % word[-1][1:])
        if 'have been cleared' in word_eol[0]: xchat.command('JOIN %s' %word[-1])
        if 'key is' in word_eol[0]:            xchat.command('JOIN %s %s' % (word[4][2:-2], word[-1][2:-2]))
        # Work around xchat stupidness by always writing chanserv notices to the
        # current context
        # Intercept akick lists if needed
        if intercept_akick:
            if 'AutoRemove' in word_eol[0] or 'Num Hostmask' in word_eol[0] or '--- --------' in word_eol[0]:
                return xchat.EAT_ALL
            if '-- End of list --' in word_eol[0]:
                intercept_akick=False
                # FIXME Remove marker
                run_pending()
            else:
                # FIXME Parse hostmask and add to bans
                pass
        if word[1] == 'NOTICE':
            xchat.emit_print("Notice", 'ChanServ', word_eol[3][2:])
            return xchat.EAT_ALL
xchat.hook_server('NOTICE', join)
xchat.hook_server('INVITE', join)

def download():
    import urllib2, os
    xchat.emit_print('Server Text','Trying to download chanserv.py from kaarsemaker.net')
    try:
        fd = open(os.path.join(xchat.get_info('xchatdir'),'chanserv.py'))
        old_cs = fd.read()
        fd.close()
        fd = urllib2.urlopen('http://media.kaarsemaker.net/chanserv.py')
        new_cs = fd.read()
        fd.close()
        if old_cs == new_cs:
            xchat.emit_print('Server Text','No new version of chanserv.py is available')
            return
        # Basic sanity check
        if 'Seveas' in new_cs and 'chanserv.py' in new_cs and 'xchat.hook_server' in new_cs:
            fd2 = open(os.path.join(xchat.get_info('xchatdir'),'chanserv.py'),'w')
            fd2.write(new_cs)
            fd2.close()
            xchat.emit_print('Server Text','chanserv.py updated -- reload with /py reload chanserv.py')
        else:
            xchat.emit_print('Server Error','Downloading chanserv.py failed - downloaded file not correct')
    except:
        xchat.emit_print('Server Error','Failed to update chanserv.py')


# Spam!
xchat.emit_print('Server Text',"Loaded %s %s by Seveas <dennis@kaarsemaker.net>" % (__module_description__, __module_version__)
```also available from [http://www.kaarsemaker.net/software/chanserv/](http://www.kaarsemaker.net/software/chanserv/)

However there's a problem.

/cs bans, and /cs u do not seem to work properly.

Both of these do a whois on the user, then /mode +bd to scan the ban lists. They then see if anything matches. The first prints results, the second undoes the ban(s).

When running through bip, the whois is performed, but that's about it. You can see the whois results in your server tab as normal.

Manually running /mode +bd causes chanserv.py to then finish running and print/unban as it should do.

Talking with Seveas on irc, he pointed to how line 384 contains "=bd" which is a typo and should actually be "+bd". Running this manually in xchat shows that bip does indeed not like = with multiple arguments, wheras it does what it should when +bd is called.

I have not been able to get things working though by "fixing" that line, and me and Seveas are out of ideas.

Checking the rawlog, there is no difference between what is sent and received when connected through bip, or directly to freenode.

Can anyone help? :)

---

### Post by PriceChild on 2008-02-17
*bump*

---

### Post by PriceChild on 2008-02-17
*bump*

---

