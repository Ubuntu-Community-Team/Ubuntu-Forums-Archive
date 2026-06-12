---
title: "ctags support for vhdl in vim - Regular Expression"
date: 2010-12-25
forum: Programming Talk
---

### Post by riforifo on 2010-12-25
Hello,

I am trying to make ctags (v 5.6) work with vhdl files in vim (with taglist plugin) . Basically I modify the ~/.ctags file like below. 

--langdef=vhdl
--langmap=vhdl:.vhd
--regex-vhdl=/^[ \t]*([^ \t:]+)[ \t]*:[ \t]*process[ \t]*\(/\1/p,processes/i
      ...
      ...

However I can't detect "port map" expressions. My coding style is like below.

i_buf_wrapper: ds_ver_4to3_buf_wrapper
 port map(

       clk                 => clk,                   --  : in  std_logic;
       rst                 => rst,                   --  : in  std_logic;
       o_de              => de
 );

Can you please guide me for a regular expression so that I can have the port map detected on my .ctags file.

thank you very much for your help
[COLOR=#888888]rifat
[/COLOR]
ps: ctags version 5.8 supports VHDL natively but frankly either I couldn't make it work or it's not good enough.

---

