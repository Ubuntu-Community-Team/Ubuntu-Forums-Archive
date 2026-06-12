---
title: "how to install amd rx vega 64 in ubuntu 16.04"
date: 2018-01-07
forum: New to Ubuntu
---

### Post by taitos12 on 2018-01-07
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]        im totally new to Ubuntu,(and sorry for my english) i have tried to  install my AMD RX VEGA 64 the way it says in AMD's site, but i can't  make it to work
  i have done this all:
  
sudo apt update sudo apt dist-upgrade sudo reboot

  
cd /tmp tar -Jxvf amdgpu-pro-17.40-483984.tar.xz.tar

  
cd amdgpu-pro-17.30-NNNNNN ./amdgpu-pro-install –y sudo reboot

  
sudo usermod -a -G video $ my user

  
sudo apt install -y rocm-amdgpu-pro

  
echo 'export LLVM_BIN=/opt/amdgpu-pro/bin' | sudo tee /etc/profile.d/amdgpu-pro.sh

  [B]
this is what the terminal shows me when i try to see if my GPU is installed[/B]

  
~$ dpkg -l amdgpu-pro 
Deseado=desconocido(U)/Instalar/eliminaR/Purgar/retener(H) | Estado=No/Inst/ficheros-Conf/desempaqUetado/medio-conF/medio-inst(H)/espera-disparo(W)/pendienTe-disparo |/ Err?=(ninguno)/requiere-Reinst (Estado,Err: mayúsc.=malo) ||/ Nombre         Versión      Arquitectura Descripción +++-==============-============-============-=================================
ii  amdgpu-pro     17.40-483984 amd64        Meta package to install amdgpu Pr

  
~$ sudo lshw -C video 
*-display
       descripción: VGA compatible controller        producto: Vega 10 XT [Radeon RX Vega 64]        fabricante: Advanced Micro Devices, Inc. [AMD/ATI]        id físico: 0        información del bus: pci@0000:03:00.0        versión: c1        anchura: 64 bits        reloj: 33MHz        capacidades: pm pciexpress msi vga_controller bus_master cap_list  rom        configuración: driver=amdgpu latency=0        recursos: irq:27 memoria:c0000000-cfffffff  memoria:dfe00000-dfffffff ioport:ee00(size=256)  memoria:fde00000-fde7ffff memoria:c0000-dffff

  
-$ clinfo Number of platforms                               0

  
~$ sudo lspci  -v -s  $(lspci | grep ' VGA ' | cut -d" " -f 1) 
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc.  [AMD/ATI] Vega 10 XT [Radeon RX Vega 64] (rev c1) (prog-if 00 [VGA  controller])     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 0b36     Flags: bus master, fast devsel, latency 0, IRQ 27     Memory at c0000000 (64-bit, prefetchable) [size=256M]     Memory at dfe00000 (64-bit, prefetchable) [size=2M]     I/O ports at ee00 [size=256]     Memory at fde00000 (32-bit, non-prefetchable) [size=512K]     [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]     Capabilities: [48] Vendor Specific Information: Len=08      Capabilities: [50] Power Management version 3     Capabilities: [64] Express Legacy Endpoint, MSI 00     Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+     Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1  Len=010      Capabilities: [150] Advanced Error Reporting     Capabilities: [200] #15     Capabilities: [270] #19     Capabilities: [2a0] Access Control Services     Capabilities: [2b0] Address Translation Service (ATS)     Capabilities: [2c0] #13     Capabilities: [2d0] #1b     Capabilities: [320] Latency Tolerance Reporting     Kernel driver in use: amdgpu     Kernel modules: amdgpu

  
~$ glxinfo | grep -i vendor server glx vendor string: AMD client glx vendor string: AMD OpenGL vendor string: Advanced Micro Devices, Inc.

  
~$ lspci | grep VGA 03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Vega 10 XT [Radeon RX Vega 64] (rev c1)

  [B]
Please[/B] if someone can help me on how to Step by Step for a baby install the GPU i'll be very thakful
[/TD]
[/TR]
[/TABLE]

---

