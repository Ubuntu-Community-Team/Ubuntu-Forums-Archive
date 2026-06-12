---
title: "cpufreq errors...."
date: 2008-08-21
forum: New to Ubuntu
---

### Post by noorez on 2008-08-21
I'm having some problems with the cpufreq-selector. It appears to have no effect for me. Here is the output for cpufreq-info:

analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: ondemand, powersave, conservative, userspace, performance
  current policy: frequency should be within 1.67 GHz and 1.67 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: ondemand, powersave, conservative, userspace, performance
  current policy: frequency should be within 1.67 GHz and 1.67 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.


The policy seems to be stuck at 1.67GHz....I changed it with cpufreq-set but it changed back when I restarted....is there a way to make it permanent?.....or restore all files back to a default setting?

---

