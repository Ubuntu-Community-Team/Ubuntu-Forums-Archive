---
title: "need help in correcting errors in fifo verilog"
date: 2011-05-28
forum: Programming Talk
---

### Post by thehermes5 on 2011-05-28
Hi,

Can u help me debug errors in the fifo code?

I am trying to find error but I have not suceeded in finding any.


module newfifo(rst,
clk, 
din,
wr_in, //write_enable signal
rd_in, // read_enable
dout, //data_out
empty,//data_in
full);


input rst,
clk;

input [7:0]din;
input wr_in,rd_in;
output [7:0]dout;

output empty,full;
reg [7:0] dout;
reg [3:0]read_ptr, write_ptr; //read and write pointers
reg [7:0] mem [14:0];



always@(posedge clk or negedge rst)
begin
if (rst)
write_ptr<=0;
else if (wr_in==1)
begin
mem[write_ptr[3:0]]<=din;
write_ptr <= write_ptr+1;
end
end

always@(posedge clk or negedge rst)
begin
if (rst)
begin
read_ptr<=0;
dout<=0;
end
else if (rd_in==1)
begin
dout<=mem[read_ptr[3:0]];
read_ptr <= read_ptr+1;
end
end



endmodule


//testbench
`timescale 1ns / 1ps


module newfifotestbench();


reg rst;

reg clk;

reg [7:0] din;

reg wr_in;

reg rd_in;

wire [7:0] dout;

wire empty;

wire full;




newfifo h1 (.rst(rst),
.clk(clk),
.din(din),
.wr_in(wr_in),
.rd_in(rd_in),
.dout(dout),
.empty(empty),
.full(full));



/*
initial begin
$shm_open("newfifo.shm");

$shm_probe(clk);

$shm_probe(rst,din,dout,wr_in,rd_in,full,empty); 

end*/

integer i;


always #10 clk=~clk;

initial

begin

clk=0;

rst=0;

#100 rst=1;

wr_in=1;

rd_in=0;

for(i=0;i<5;i=i+1)

begin

#20 din[7:0]=8'b10101010;

#20 din[7:0]=8'b11001100;

#20 din[7:0]=8'b11111111; 

end

wr_in=0;

rd_in=1;



#1000; 
end
endmodule


The problems that I am facing are:
dout signal always stays at 0000000 inspite of my read_en going high.
Secondly, can u give me tips on how to write statement for empty and full.
Kindly excuse me if there are any mistakes as I am a beginner.
Thanks in advance.[IMG]http://images.elektroda.net/92_1306588874.png[/IMG]

---

