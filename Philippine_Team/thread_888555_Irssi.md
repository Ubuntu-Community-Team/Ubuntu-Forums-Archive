---
title: "Irssi"
date: 2008-08-13
forum: Philippine Team
---

### Post by initial_m on 2008-08-13
Anybody here using this IRC on terminal, la lang, parang maganda gamitin eh, nag try ako pero d ko lam panu ko mag coconect, lagi refused..:(

---

### Post by Jucato on 2008-08-13
Pag nasa irssi ka na, type:

```
/server irc.ubuntu.com 8001
```

basically

/server <IRC Server> <port>

port is optional

---

### Post by daxumaming on 2008-08-13
Here's the howto: [http://www.irssi.org/documentation/startup](http://www.irssi.org/documentation/startup)

and here's my config file so it'll auto-connect everytime i login

```

servers = (
  {
    address = "irc.freenode.net";
    chatnet = "Freenode";
    port = "8001";
    use_ssl = "no";
    ssl_verify = "no";
    autoconnect = "yes";
  },
);

chatnets = {
  Freenode = {
    type = "IRC";
    autosendcmd = "/msg nickserv identify myPasswordHere;wait 2000";
  };
};

channels = (
  { name = "#ubuntu-meeting"; chatnet = "Freenode"; autojoin = "yes"; },
  { name = "#ubuntu-ph"; chatnet = "Freenode"; autojoin = "yes"; },
  { name = "#ubuntu-bugs"; chatnet = "Freenode"; autojoin = "yes"; },
  { name = "#ubuntu-motu"; chatnet = "Freenode"; autojoin = "yes"; },
  { name = "#ubuntu-devel"; chatnet = "Freenode"; autojoin = "yes"; },
  { name = "#kubuntu-devel"; chatnet = "Freenode"; autojoin = "yes"; },
  { name = "#xubuntu-devel"; chatnet = "Freenode"; autojoin = "yes"; }
);

aliases = {
  J = "join";
  WJOIN = "join -window";
  WQUERY = "query -window";
  DATE = "time";
  HOST = "userhost";
  LAST = "lastlog";
  WI = "whois";
  WW = "whowas";
  W = "who";
  N = "names";
  M = "msg";
  T = "topic";
  K = "kick";
  KB = "kickban";
  BANS = "ban";
  B = "ban";
  MUB = "unban *";
  UB = "unban";
  IG = "ignore";
  UNIG = "unignore";
  SB = "scrollback";
  UMODE = "mode $N";
  WC = "window close";
  RUN = "SCRIPT LOAD";
  SBAR = "STATUSBAR";
  INVITELIST = "mode $C +I";
  Q = "QUERY";
  EXEMPTLIST = "mode $C +e";
  CS = "/msg chanserv";
  nsident = "/msg nickserv identify !Venom1";
  NS = "/msg nickserv";
};

statusbar = {
  # formats:
  # when using {templates}, the template is shown only if it's argument isn't
  # empty unless no argument is given. for example {sb} is printed always,
  # but {sb $T} is printed only if $T isn't empty.

  items = {
    # start/end text in statusbars
    barstart = "{sbstart}";
    barend = "{sbend}";

    topicbarstart = "{topicsbstart}";
    topicbarend = "{topicsbend}";

    # treated "normally", you could change the time/user name to whatever
    time = "{sb $Z}";
    user = "{sb {sbnickmode $cumode}$N{sbmode $usermode}{sbaway $A}}";

    # treated specially .. window is printed with non-empty windows,
    # window_empty is printed with empty windows
    window = "{sb $winref:$itemname{sbmode $M}}";
    window_empty = "{sb $winref{sbservertag $tag}}";
    prompt = "{prompt $[.15]itemname}";
    prompt_empty = "{prompt $winname}";
    topic = " $topic";
    topic_empty = " Irssi v$J - http://irssi.org/help/";

    # all of these treated specially, they're only displayed when needed
    lag = "{sb Lag: $0-}";
    act = "{sb Act: $0-}";
    more = "-- more --";
  };

  # there's two type of statusbars. root statusbars are either at the top
  # of the screen or at the bottom of the screen. window statusbars are at
  # the top/bottom of each split window in screen.
  default = {
    # the "default statusbar" to be displayed at the bottom of the window.
    # contains all the normal items.
    window = {
      disabled = "no";

      # window, root
      type = "window";
      # top, bottom
      placement = "bottom";
      # number
      position = "1";
      # active, inactive, always
      visible = "active";

      # list of items in statusbar in the display order
      items = {
        barstart = { priority = "100"; };
        time = { };
        user = { };
        window = { };
        window_empty = { };
        lag = { priority = "-1"; };
        act = { priority = "10"; };
        more = { priority = "-1"; alignment = "right"; };
        barend = { priority = "100"; alignment = "right"; };
      };
    };

    # statusbar to use in inactive split windows
    window_inact = {
      type = "window";
      placement = "bottom";
      position = "1";
      visible = "inactive";
      items = {
        barstart = { priority = "100"; };
        window = { };
        window_empty = { };
        more = { priority = "-1"; alignment = "right"; };
        barend = { priority = "100"; alignment = "right"; };
      };
    };

    # we treat input line as yet another statusbar :) It's possible to
    # add other items before or after the input line item.
    prompt = {
      type = "root";
      placement = "bottom";
      # we want to be at the bottom always
      position = "100";
      visible = "always";
      items = {
        prompt = { priority = "-1"; };
        prompt_empty = { priority = "-1"; };
        # treated specially, this is the real input line.
        input = { priority = "10"; };
      };
    };

    # topicbar
    topic = {
      type = "root";
      placement = "top";
      position = "1";
      visible = "always";
      items = {
        topicbarstart = { priority = "100"; };
        topic = { };
        topic_empty = { };
        topicbarend = { priority = "100"; alignment = "right"; };
      };
    };
  };
};
settings = {
  core = {
    real_name = "Dax Solomon Umaming";
    user_name = "dax";
    nick = "Knightlust";
  };
  "fe-text" = { autostick_split_windows = "no"; };
};
windows = {
  4 = {
    items = (
      {
        type = "CHANNEL";
        chat_type = "IRC";
        name = "#ubuntu-bugs";
        tag = "Freenode";
      }
    );
    sticky = "yes";
  };
  2 = {
    items = (
      {
        type = "CHANNEL";
        chat_type = "IRC";
        name = "#ubuntu-meeting";
        tag = "Freenode";
      }
    );
  };
  3 = {
    items = (
      {
        type = "CHANNEL";
        chat_type = "IRC";
        name = "#ubuntu-ph";
        tag = "Freenode";
      }
    );
  };
  5 = {
    items = (
      {
        type = "CHANNEL";
        chat_type = "IRC";
        name = "#ubuntu-motu";
        tag = "Freenode";
      }
    );
  };
  8 = {
    items = (
      {
        type = "CHANNEL";
        chat_type = "IRC";
        name = "#xubuntu-devel";
        tag = "Freenode";
      }
    );
  };
  7 = {
    items = (
      {
        type = "CHANNEL";
        chat_type = "IRC";
        name = "#kubuntu-devel";
        tag = "Freenode";
      }
    );
  };
  6 = {
    items = (
      {
        type = "CHANNEL";
        chat_type = "IRC";
        name = "#ubuntu-devel";
        tag = "Freenode";
      }
    );
  };
  1 = { immortal = "yes"; name = "(status)"; level = "ALL"; };
};
mainwindows = {
  3 = { first_line = "23"; lines = "21"; };
  4 = { first_line = "1"; lines = "22"; };
};


```

---

### Post by daxumaming on 2008-08-13
sorry, double post

---

### Post by jsgotangco on 2008-08-13
> **initial_m said:**
> Anybody here using this IRC on terminal, la lang, parang maganda gamitin eh, nag try ako pero d ko lam panu ko mag coconect, lagi refused..:(

you might want to try out weechat

---

