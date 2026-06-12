---
title: "What is wrong with my code??"
date: 2011-03-19
forum: Programming Talk
---

### Post by aji sydin on 2011-03-19
I AM A NEWBIE IN VERILOG AND JUST DONT KNOW WHAT IS WRONG WITH MY CODE.
THIS IS THE CRAZY SIMPLE QUESTION : 

Develop a Verilog model for a thermostat that has two 8-bit unsigned binary inputs representing the target temperature and the actual temperature in degrees Fahrenheit (&#730;F). Assume that both temperatures are above freezing (32&#730;F). The detector has two outputs: one to turn a heater on when the actual temperature is more than 5&#730;F below target, and one to turn a cooler onwhen the actual temperature is more than 5&#730;F above target.

AND THIS IS MY CODE:

module*C2*(switch,clk,heater_on,cooler_on,enable_a ctual,enable_target);


input clk;
input enable_actual,enable_target;
input*[7:0]*switch*;
reg [7:0]*actual,target;
output* heater_on,*cooler_on;

always @(posedge clk) 
begin 
if (enable_actual) actual <= switch;

else if (enable_target) target <= switch;

end 

assign*heater_on*=*actual*<*target*-*5;
assign*cooler_on*=*actual*>*target*+*5;

endmodule

IT DIDN'T SHOW ANY ERROR DURING COMPILATION.THE PROBLEM IS THAT THE OUTPUT WHICH HEATER_ON AND COOLER_ON DIDN'T ON CORRECTLY.WHAT IS WRONG WITH MY CODE??CAN SOMEBODY PLS HELP ME.

PICTURE2 IS THE SIMULATION WHEN I WANT THE HEATER_ON ONLY TO BE ON
PICTURE4 IS THE SIMULATION WHEN I WANT THE COOLER_ON ONLY TO BE ON

BUT THE SIMULATION WAS NOT WHAT I EXPECTED FOR:HELP PLS:popcorn:

---

### Post by Sef on 2011-03-19
Moved to Programming Talk.

---

