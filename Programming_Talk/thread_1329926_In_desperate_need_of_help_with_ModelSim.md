---
title: "In desperate need of help with ModelSim"
date: 2009-11-17
forum: Programming Talk
---

### Post by BlackSwordD2 on 2009-11-17
writing my first program in VHDL due tomorrow and i cant get the bloody thing to simulate. when i do i get this message

> 
# Compile of 2x1Mux.vhdl was successful.
# Compile of 4x1Mux.vhdl was successful.
# Compile of ALU_2.vhdl was successful.
# Compile of and_gate.vhdl was successful.
# Compile of Half_Adder.vhdl was successful.
# Compile of not_gate.vhdl was successful.
# Compile of or_gate.vhdl was successful.
# Compile of 4_alu.vhdl was successful.
# 8 compiles, 0 failed with no errors. 
vsim ALU_Lib.onebitalu
# vsim ALU_Lib.onebitalu 
# Loading std.standard
# Loading ALU_Lib.onebitalu(structure)
# Loading ALU_Lib.and_gate(structure_view)
# ** Failure: (vsim-3817) Port "i1" of entity "and_gate" is not in the component being instantiated.
#    Time: 0 ns  Iteration: 0  Instance: /onebitalu/a1 File: C:/Users/***/Desktop/and_gate.vhdl Line: 2
# ** Failure: (vsim-3817) Port "i2" of entity "and_gate" is not in the component being instantiated.
#    Time: 0 ns  Iteration: 0  Instance: /onebitalu/a1 File: C:/Users/***/Desktop/and_gate.vhdl Line: 2
# ** Error: (vsim-3732) C:/Users/***/Desktop/ALU_2.vhdl(35): No default binding for component at 'a1'.
#  (Port 'l2' is not on the entity.)
#         Region: /onebitalu/a1
# ** Error: (vsim-3732) C:/Users/***/Desktop/ALU_2.vhdl(35): No default binding for component at 'a1'.
#  (Port 'l1' is not on the entity.)
#         Region: /onebitalu/a1
# Fatal error in Process line__9 at C:/Users/***/Desktop/and_gate.vhdl line 9
#  while elaborating region: /onebitalu/a1
# Load interrupted
# Error loading design


for the whole process i have uploaded the said files i compiled, clicked "compile all" then "start simulation". when i do the same process with any of my gates, adders or multiplexers they run flawlessly but not my onebitalu or 4_alu. being as my 4_alu calls my onebitalu, i have just been trying to simulate my onebitalu

---

