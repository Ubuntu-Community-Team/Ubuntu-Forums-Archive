---
title: "Trouble compiling custom Linux kernel (v3.2)"
date: 2012-02-24
forum: Packaging and Compiling Programs
---

### Post by MDL1983 on 2012-02-24
Hello,

Please disregard this message if this is the wrong place to be posting this. I have been trying to compile a custom kernel that I checked out of a third party repository and am having some trouble building it. I am somewhat of a Linux novice, and the error messages are cryptic to me, so I was hoping perhaps someone could help clear things up.

Everything seems to be working fine until the second stage of the process where the modules are built.

I simply ran make menuconfig to make a config file, and then run make after this; nothing more. The kernel compiles but fails at the linker stage saying there are "module mismatches" and recommending I run "make CONFIG_DEBUG_SECTION_MISMATCH=y" instead, so I did. The output I get (starting at the second stage) at this point is as follows:



```
Kernel: arch/x86/boot/bzImage is ready  (#2)
  Building modules, stage 2.
  MODPOST 3404 modules
WARNING: drivers/mfd/cs5535-mfd.o(.data+0x70): Section mismatch in reference from the variable cs5535_mfd_drv to the function .devinit.text:cs5535_mfd_probe()
The variable cs5535_mfd_drv references
the function __devinit cs5535_mfd_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*driver, *_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/mfd/cs5535-mfd.o(.data+0x74): Section mismatch in reference from the variable cs5535_mfd_drv to the function .devexit.text:cs5535_mfd_remove()
The variable cs5535_mfd_drv references
the function __devexit cs5535_mfd_remove()
If the reference is valid then annotate the
variable with __exit* (see linux/init.h) or name the variable:
*driver, *_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/3com/3c509.o(.data+0x1bc): Section mismatch in reference from the variable el3_eisa_driver to the function .init.text:el3_eisa_probe()
The variable el3_eisa_driver references
the function __init el3_eisa_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/3com/3c509.o(.data+0x1e0): Section mismatch in reference from the variable el3_mca_driver to the variable .init.data:el3_mca_adapter_ids
The variable el3_mca_driver references
the variable __initdata el3_mca_adapter_ids
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/3com/3c509.o(.data+0x204): Section mismatch in reference from the variable el3_mca_driver to the function .init.text:el3_mca_probe()
The variable el3_mca_driver references
the function __init el3_mca_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/3com/3c59x.o(.data+0xdc): Section mismatch in reference from the variable vortex_eisa_driver to the function .init.text:vortex_eisa_probe()
The variable vortex_eisa_driver references
the function __init vortex_eisa_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/8390/ne3210.o(.data+0x5c): Section mismatch in reference from the variable ne3210_eisa_driver to the function .init.text:ne3210_eisa_probe()
The variable ne3210_eisa_driver references
the function __init ne3210_eisa_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/8390/smc-mca.o(.data+0x0): Section mismatch in reference from the variable ultra_driver to the variable .init.data:smc_mca_adapter_ids
The variable ultra_driver references
the variable __initdata smc_mca_adapter_ids
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/8390/smc-mca.o(.data+0x24): Section mismatch in reference from the variable ultra_driver to the function .init.text:ultramca_probe()
The variable ultra_driver references
the function __init ultramca_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/amd/depca.o(.data+0x44): Section mismatch in reference from the variable depca_mca_driver to the function .init.text:depca_mca_probe()
The variable depca_mca_driver references
the function __init depca_mca_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/amd/depca.o(.data+0x9c): Section mismatch in reference from the variable depca_eisa_driver to the function .init.text:depca_eisa_probe()
The variable depca_eisa_driver references
the function __init depca_eisa_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/amd/depca.o(.devinit.text+0x1b): Section mismatch in reference from the function depca_isa_probe() to the function .init.text:depca_common_init()
The function __devinit depca_isa_probe() references
a function __init depca_common_init().
If depca_common_init is only used by depca_isa_probe then
annotate depca_common_init with a matching annotation.

WARNING: drivers/net/ethernet/amd/depca.o(.devinit.text+0x2e): Section mismatch in reference from the function depca_isa_probe() to the function .init.text:depca_shmem_probe()
The function __devinit depca_isa_probe() references
a function __init depca_shmem_probe().
If depca_shmem_probe is only used by depca_isa_probe then
annotate depca_shmem_probe with a matching annotation.

WARNING: drivers/net/ethernet/amd/depca.o(.devinit.text+0x65): Section mismatch in reference from the function depca_isa_probe() to the function .init.text:depca_hw_init()
The function __devinit depca_isa_probe() references
a function __init depca_hw_init().
If depca_hw_init is only used by depca_isa_probe then
annotate depca_hw_init with a matching annotation.

WARNING: drivers/net/ethernet/dec/tulip/de4x5.o(.data+0xbc): Section mismatch in reference from the variable de4x5_eisa_driver to the function .init.text:de4x5_eisa_probe()
The variable de4x5_eisa_driver references
the function __init de4x5_eisa_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/hp/hp100.o(.data+0x7c): Section mismatch in reference from the variable hp100_eisa_driver to the function .init.text:hp100_eisa_probe()
The variable hp100_eisa_driver references
the function __init hp100_eisa_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/ethernet/natsemi/ibmlana.o(.data+0x0): Section mismatch in reference from the variable ibmlana_driver to the variable .init.data:ibmlana_adapter_ids
The variable ibmlana_driver references
the variable __initdata ibmlana_adapter_ids
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/net/tokenring/madgemc.o(.data+0x0): Section mismatch in reference from the variable madgemc_driver to the variable .init.data:madgemc_adapter_ids
The variable madgemc_driver references
the variable __initdata madgemc_adapter_ids
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/scsi/NCR_Q720_mod.o(.data+0x24): Section mismatch in reference from the variable NCR_Q720_driver to the function .init.text:NCR_Q720_probe()
The variable NCR_Q720_driver references
the function __init NCR_Q720_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/scsi/sim710.o(.data+0x64): Section mismatch in reference from the variable sim710_mca_driver to the function .init.text:sim710_mca_probe()
The variable sim710_mca_driver references
the function __init sim710_mca_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/scsi/sim710.o(.data+0xbc): Section mismatch in reference from the variable sim710_eisa_driver to the function .init.text:sim710_eisa_probe()
The variable sim710_eisa_driver references
the function __init sim710_eisa_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/spi/spi-gpio.o(.devinit.text+0x3d): Section mismatch in reference from the function spi_gpio_probe() to the function .init.text:spi_gpio_request()
The function __devinit spi_gpio_probe() references
a function __init spi_gpio_request().
If spi_gpio_request is only used by spi_gpio_probe then
annotate spi_gpio_request with a matching annotation.

WARNING: drivers/spi/spi-topcliff-pch.o(.data+0x70): Section mismatch in reference from the variable pch_spi_pcidev to the function .devinit.text:pch_spi_probe()
The variable pch_spi_pcidev references
the function __devinit pch_spi_probe()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*driver, *_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/spi/spi-topcliff-pch.o(.data+0x74): Section mismatch in reference from the variable pch_spi_pcidev to the function .devexit.text:pch_spi_remove()
The variable pch_spi_pcidev references
the function __devexit pch_spi_remove()
If the reference is valid then annotate the
variable with __exit* (see linux/init.h) or name the variable:
*driver, *_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: drivers/staging/comedi/drivers/s626.o(.text+0x238d): Section mismatch in reference from the function s626_attach() to the variable .devinit.rodata:s626_pci_table
The function s626_attach() references
the variable __devinitconst s626_pci_table.
This is often because s626_attach lacks a __devinitconst 
annotation or the annotation of s626_pci_table is wrong.

WARNING: drivers/staging/comedi/drivers/s626.o(.text+0x2393): Section mismatch in reference from the function s626_attach() to the variable .devinit.rodata:s626_pci_table
The function s626_attach() references
the variable __devinitconst s626_pci_table.
This is often because s626_attach lacks a __devinitconst 
annotation or the annotation of s626_pci_table is wrong.

WARNING: drivers/staging/comedi/drivers/s626.o(.text+0x2399): Section mismatch in reference from the function s626_attach() to the variable .devinit.rodata:s626_pci_table
The function s626_attach() references
the variable __devinitconst s626_pci_table.
This is often because s626_attach lacks a __devinitconst 
annotation or the annotation of s626_pci_table is wrong.

WARNING: drivers/staging/comedi/drivers/s626.o(.text+0x23a1): Section mismatch in reference from the function s626_attach() to the variable .devinit.rodata:s626_pci_table
The function s626_attach() references
the variable __devinitconst s626_pci_table.
This is often because s626_attach lacks a __devinitconst 
annotation or the annotation of s626_pci_table is wrong.

WARNING: drivers/usb/gadget/g_ffs.o(.text+0x6c53): Section mismatch in reference from the function eth_bind_config() to the function .init.text:geth_bind_config()
The function eth_bind_config() references
the function __init geth_bind_config().
This is often because eth_bind_config lacks a __init 
annotation or the annotation of geth_bind_config is wrong.

ERROR: "__modver_version_show" [drivers/staging/rts5139/rts5139.ko] undefined!
make[1]: *** [__modpost] Error 1
make: *** [modules] Error 2
```


-------------------------

Does this indicate that there are issues with the actual code or am I setting my config file up wrong somehow?

I really just want to compile this, but have no idea what needs to be done. Any pointers welcome, and let me know if I can provide more info.

Thanks!

--MDL

---

### Post by elliotn on 2012-02-24
why do u need to compile a custom kernel?

---

### Post by MDL1983 on 2012-02-24
Roelforg:

Thank you, and my apologies. I decided the kernel wasn't a "program" in my head for some reason when skimming topic titles.

Elliotn:

We're testing some USB3 driver changes not present in the kernel mainline.

---

### Post by oldos2er on 2012-02-24
Thread moved to Packaging and Compiling Programs.

---

### Post by Bachstelze on 2012-02-24
Looks like your configuration is wrong. Try copying the configuration of the current kernel and start from there

```
cp /boot/config-... .config
make oldconfig
```

---

