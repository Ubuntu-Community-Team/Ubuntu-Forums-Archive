---
title: "Problem viewing waveforms using gtkwave"
date: 2010-09-28
forum: Programming Talk
---

### Post by mohitdaksh on 2010-09-28
Hey.. I am new to VHDL and I was trying to simulate a simple halfadder circuit. I created a testbench. But I am not sure whether its correct or not. I am using ghdl to analyze the code and create VCD file which then should be read by gtkwave for waveforms. This is my code:
```
library IEEE;
use IEEE.std_logic_1164.all;

entity ha is
port(a,b : in bit;
s,c : out bit);
end ha;
architecture haa of ha is
begin
s<=a xor b;
c<=a and b;
end haa;



entity testbench is
end testbench;

architecture test of testbench is
signal int1,int2,sum,carry : bit;

component ha is
port(a,b : in bit;
s,c : out bit);
end component;

begin
process
begin
int1<='1';
int2<='0';
wait for 4 ns;
int1<='1';
int2<='1';

wait ;
end process;
u1: ha port map(int1,int2,sum,carry);
end test;

```

Everything goes fine but when I give the command to view the waveforms in gtkwave the following shows up:

> 
GTKWave Analyzer v3.3.2 (w)1999-2010 BSI

[0] start time.
[0] end time.
VCD times range is equal to zero.  Exiting.

Can anyone tell why is it happening?  Thanks in advance

---

