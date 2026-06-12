---
title: "issues with vscodium and lua"
date: 2024-01-11
forum: Programming Talk
---

### Post by Unguidedone on 2024-01-11
I am trying to get away from visual studio code and it does work really well almost no problems using it.  But I want to use vscodium instead.  so i got a few different issues.  I want to use my systems install of lua and not a downloaded plugin because it just does not work on vscodium.  

now if i run: which lua
output: /usr/local/bin/lua  <-- i want vscodium to use this location instead of:  /bin/sh


[COLOR=#cccccc][FONT=Droid Sans Mono][COLOR=#6796e6][Running][/COLOR][COLOR=#ce9178] lua "/home/user/a.lua"[/COLOR]

[COLOR=#cccccc]/bin/sh: line 1: lua: command not found  <---  its using the wrong location, a place that does not have lua installed.  where can i find this location and make the edit to the correct location[/COLOR]


[COLOR=#6796e6][Done][/COLOR][COLOR=#ce9178] exited with [/COLOR][COLOR=#f44747]code=127[/COLOR][COLOR=#ce9178] in [/COLOR][COLOR=#b5cea8]0.004[/COLOR][COLOR=#ce9178] seconds   <--  exit code 127 means the language is not found or not installed on the system[/COLOR]



[/FONT][/COLOR]

i have been everywhere in the programs config and i cant find the location in the configs.  what am i missing?

i found this file:
/home/***/.var/app/com.vscodium.codium/config/VSCodium/User/settings.json

{
    "lua-local.interpreter": "/usr/local/bin/lua",    <------- this is the correct location but codium is using an alt location  where do i edit to fix this???
    "code-runner.defaultLanguage": "lua",
    "lua.debug.settings.console": "externalTerminal",
    "terminal.external.linuxExec": "x-terminal-emulator",
    "terminal.integrated.automationProfile.linux": {},
    "terminal.integrated.defaultProfile.linux": "bash",
    "terminal.explorerKind": "external"
}


i cant find the config :(
find / -type f -exec grep -H '/bin/sh' {} \;     // my attempt at finding the config file by keyword in file and it failed to show anything useful.

i might just have to go back to vscode.

i want codium to use my systems terminal and not its internal terminal this would solve ALL issues.  but the configs to change this elude me....

---

