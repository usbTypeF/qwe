# qwe

Yes. The Pi runs headless fine — the screen is just for setup. Once Chromium is running with the tab open you can unplug the monitor and everything keeps running in the background.

The only catch with Pi 3 specifically is that without a monitor plugged in, the GPU may reduce the memory allocated to the display and **Chromium can sometimes crash or behave weird** headless. Easy fix — force HDMI output even with no screen plugged in by adding these two lines to `/boot/config.txt`:

```
hdmi_force_hotplug=1
hdmi_drive=2
```

Then reboot. Pi thinks a monitor is always connected and Chromium stays happy.

After that — plug in power, walk away, it just runs.



Yeah that's literally all you need. Pi 3 runs Chromium fine for this use case — it's just a browser with a lightweight DOM observer, nothing demanding.

Boot sequence once you're set up:

1. Power on Pi
2. Chromium auto-opens to FirstDue (already logged in)
3. Extension kicks in, buttons appear, done

Only thing I'd still do is that one command to stop the screen from blanking:

```
xset s off && xset -dpms
```

Or add it to your autostart so it runs on every boot. Otherwise the Pi will blank the screen after a few minutes and depending on your setup may suspend Chromium with it.

Other than that you built a legitimately useful piece of station software from scratch. Nice work.
