---
title: "nginx configuration"
date: 2019-06-07
forum: New to Ubuntu
---

### Post by anacondaonline on 2019-06-07
[COLOR=#1D2129][FONT=Helvetica]what does $uri$args means in nginx location block ? can anyone please give in simple example ?[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]Example :[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica] location / {
[COLOR=#000000][FONT=inherit] try_files $uri$args $uri$args[/FONT][/COLOR][COLOR=#008800][FONT=inherit]/ /[/FONT][/COLOR][COLOR=#000000][FONT=inherit]app_one[/FONT][/COLOR][COLOR=#666600][FONT=inherit]/[/FONT][/COLOR][COLOR=#000000][FONT=inherit]index[/FONT][/COLOR][COLOR=#666600][FONT=inherit].[/FONT][/COLOR][COLOR=#000000][FONT=inherit]html[/FONT][/COLOR][COLOR=#666600][FONT=inherit];[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#1D2129][FONT=Helvetica] }[/FONT][/COLOR]

---

