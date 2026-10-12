# PCI-Z - Vendor and Device IDs for PCI Express Hardware

[![Open PCI-Z](https://img.shields.io/badge/Open-PCI--Z-3f3f46?style=flat-square&logo=windows&logoColor=white)](https://hostonsuzanna.github.io/.github/pci-z-hardware)

## Why the Full Tuple Matters

A request for "the Realtek ID" is incomplete. Two boards can share a device ID and ship different subsystem IDs for different PHY layouts, different option ROMs, or different OEM tweaks. PCI-Z shows vendor, device, subsystem, and class together so a pack index or a forum post uses the whole tuple. Searching only the vendor ID returns a company. Searching the full line returns a candidate package.

Device Manager will eventually show the same IDs behind a details tab. PCI-Z puts them on one screen for every function, which is faster when a white-box desktop has several unknown rows and you are copying them into a note. The friendly name, if Windows has one, is a label. The codes are the identity.

## Fields on the List

| Field | Meaning | How people misuse it |
|---|---|---|
| Vendor | Silicon or board vendor code | Treating it as a model name |
| Device | The function's device code | Ignoring a second function on the same card |
| Subsystem | Board-specific pair | Skipping it because the device ID "looked enough" |
| Class | Network, storage, display, bridge, serial bus | Assuming class tells you the driver vendor |
| Bus location | Which root port the function sits behind | Confusing location with identity |

A dual-function card deserves two lines in your notes. Audio plus HDMI, or LAN plus a management function, will not collapse into one INF just because they share a bracket.

## Beside Other Tools

Copy the IDs into a driver pack search or compare them with the INF you are about to force. If PCI-Z and Device Manager disagree about the friendly name, trust the IDs. Friendly names are inherited from whatever driver bound last, including a wrong one. The codes do not change because a package guessed.

USB devices do not appear here merely because they are plugged into a rear port. This is the PCI bus, including devices that sit behind an onboard USB controller only in the sense that the controller itself is a PCI function. The phone, the stick, and the headset belong in a USB tool. Mixing those lists is how a Wi-Fi ID gets compared to a dongle.

## Machines It Suits

White-box desktops, add-in capture cards, and small boards with no silkscreen you can read are the natural fit. A sealed laptop still shows its internal PCI functions, but the OEM model number is often more useful than a raw ID once you have it, because the vendor's package is indexed by model. Use PCI-Z on that laptop to confirm you are about to install a package that lists the subsystem you actually see.

Virtual machines expose only the chipset the hypervisor emulated. A long list of vendor-specific cards inside a guest usually means you are looking at the host by mistake. Check the window title and the machine before you copy an ID into a ticket for the wrong computer.

## Reading Order

1. Confirm you are on the PC that has the unknown device.  
2. Find the class that matches the symptom: Net, Display, Storage, or a simple unknown function.  
3. Copy vendor, device, and subsystem as one line.  
4. Compare that line to the INF or the pack hit before you install.  
5. If nothing matches, stop. A nearby device ID is not a match.  

## What You Can Learn from Location

Bus location does not name the chip, but it explains a dead slot. A function that vanishes until a BIOS option enables the M.2 or the second LAN is not a missing driver. Reseat and firmware questions come before INF questions when the function is absent from PCI-Z entirely. If PCI-Z cannot see it, Windows cannot bind it, and no pack will invent the device.

## Limits

A powered-off slot or a disabled root port hides everything behind it. Thunderbolt and some docks enumerate late; refresh after the dock is actually connected. PCI-Z will not update firmware, will not toggle a BIOS option, and will not tell you which driver version is stable. It tells you the identity of a function the bus already exposed.

![PCI-Z window listing vendor, device, and subsystem codes](https://www.drwindows.de/news/wp-content/uploads/2014/01/pci-z_pgb.png)

## Common Mixups

The friendly name says the old vendor after a card swap. The IDs are the new card. Follow the IDs.  
Two identical NICs show the same device ID and different bus locations. Your note needs both, or you will disable the wrong port from a script later.  
A search result matches vendor and device and ignores subsystem. Open the INF and look for the subsystem line before you call it your driver.  
The tool shows a bridge and the user expected a disk. The disk may be behind that bridge and may be a different class. Do not install a storage driver onto a bridge entry because the names sat near each other.

## Shop Note

Keep PCI-Z next to the pack installer, not instead of it. The thirty seconds spent copying the tuple save the hour spent removing a driver that belonged to a different subsystem. That is the entire product. Shops that already know every board by sight will barely open it. Shops that see odd cards all week will use it more than the bigger tools.

## Writing the ID Down

A useful note fits on one line: vendor, device, subsystem, class, and the slot or the rear-port label if you know it. That line can be pasted into a pack search on another PC, into a ticket, or into a folder name next to the INF you finally trusted. Screenshots of the whole window are harder to search later and they omit nothing you needed beyond that line.

If you are comparing two cards that the owner says are identical, the line will either match or it will not. A match means the driver question is real. A mismatch means you are about to reuse a package across two different subsystems, which is how a "same looking" NIC ends up without a link. PCI-Z is the cheapest way to refuse that reuse.

Refresh the list after a BIOS change that enables an M.2 lane or a second LAN. Functions that were absent are not a driver failure, and functions that appear only after the change should be copied again. The old note describes the old bus.

## Search Lines

pci-z, pci z hardware id, pcie device list, pci-z vendor id, subsystem id tool, pci device codes, identify pcie card, pci-z windows, pci ven dev sub
