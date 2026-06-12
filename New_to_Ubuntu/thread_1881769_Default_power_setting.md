---
title: "Default power setting"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Viva on 2011-11-16
The default power setting in the power manager when power is critically low is blank. I accidentally changed it to hibernate, but I can't change it back. I don't want my laptop to hibernate or shutdown when the power is low. How do I change the value back to default? There are only two options available, hibernate and shut down.

---

### Post by cmcanulty on 2011-12-06
what version are you using ie 10.10, 11.10 etc?Also did you unlock the power settings also open config editor and try setting it under apps-gnome-power manager

---

### Post by bluexrider on 2011-12-06
> **cmcanulty said:**
> what version are you using ie 10.10, 11.10 etc?Also did you unlock the power settings also open config editor and try setting it under apps-gnome-power manager

run the code:

gconftool-2 -R /apps/gnome-power-manager

all can be changed via gconf-editor

Example Output
/apps/gnome-power-manager/notify:
  perhaps_recall = true
  sleep_failed = true
  sleep_failed_uri = 
  fully_charged = false
  low_capacity = true
  discharging = true
  low_power = true
 /apps/gnome-power-manager/lock:
  suspend = true
  blank_screen = false
  use_screensaver_settings = false
  hibernate = true
  gnome_keyring_hibernate = true
  gnome_keyring_suspend = false
 /apps/gnome-power-manager/ui:
  icon_policy = charge
  enable_sound = true
  show_actions = true
 /apps/gnome-power-manager/actions:
  low_ups = suspend
  sleep_type_ac = suspend
  critical_battery = suspend
  event_when_closed_battery = true
  sleep_type_battery = suspend
  critical_ups = shutdown
 /apps/gnome-power-manager/disks:
  spindown_timeout_battery = 60
  spindown_enable_ac = true
  spindown_timeout_ac = 600
  spindown_enable_battery = true
 /apps/gnome-power-manager/thresholds:
  time_low = 1200
  time_action = 120
  percentage_critical = 3
  percentage_low = 10
  percentage_action = 2
  time_critical = 300
 /apps/gnome-power-manager/statistics:
  show_axis_labels = true
  show_events = true
  graph_type = power
  smooth_data = true
  data_max_time = 21600
 /apps/gnome-power-manager/buttons:
  suspend = suspend
  lid_ac = suspend
  lid_battery = suspend
  hibernate = hibernate
  power = interactive
 /apps/gnome-power-manager/general:
  use_profile_time = true
  check_type_cpu = false
  installed_schema = 3
  use_time_for_policy = true
  network_sleep = false
 /apps/gnome-power-manager/timeout:
  sleep_computer_ac = 0
  sleep_display_ac = 300
  sleep_display_ups = 600
  sleep_computer_battery = 1800
  sleep_computer_ups = 1800
  sleep_display_battery = 600
 /apps/gnome-power-manager/backlight:
  idle_dim_battery = true
  dpms_method_battery = off
  idle_dim_time = 10
  enable = true
  idle_dim_ac = false
  battery_reduce = true
  brightness_ac = 100
  dpms_method_ac = off
  brightness_dim_battery = 50
  idle_brightness = 30

---

