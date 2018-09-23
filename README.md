# Intro
Tested on Windows 10 x64 17134.48 build. Doesnt require test mode.

# Why
Old mouse with no native 1000hz support within official drivers

# Credits
Sweetlow http://www.overclock.net/forum/members/487209-sweetlow.html

original guide http://www.overclock.net/forum/375-mice/1589644-usb-mouse-hard-overclocking-2000-hz.html

# Tools (included in this repo)
filter driver (use patch folder) http://www.overclock.net/forum/375-mice/1597441-digitally-signed-sweetlow-1000hz-mouse-driver-75.html#post27147889

atsiv to load driver https://www.google.com/search?q=atsiv+download&oq=atsiv

devcon to restart mouse  https://docs.microsoft.com/en-us/windows-hardware/drivers/devtest/devcon

hidusbf to install non patched driver http://www.overclock.net/attachments/45829

# Install
## eXtract
Unzip files from MAIN folder to "C:\Program Files\atsiv"

![N|Solid](https://lh3.googleusercontent.com/-aYz796WNAqk/WwFjGJ5EwZI/AAAAAAAAVmQ/Se8QIPd4snsHYrmnUK5C2mrgYJvCG9fzwCHMYCw/s0/explorer_2018-05-20_14-59-17.png)

## Get mouse ID
So we can use it to restart mouse. Open Powershell with admin rights
```sh
cd "C:\Program Files\atsiv"
.\devcon.exe find *mouse*
```
![N|Solid](https://lh3.googleusercontent.com/-o-2Pp52L-2I/WwFkICAmTiI/AAAAAAAAVmY/cYIYEs8hSeMI1ulv6xLB2SuRdWWqESSTQCHMYCw/s0/powershell_2018-05-20_15-03-40.png)

My ID is VID_093A

## Restore original driver & setup 1000hz 
Run EXTRA\Setup.exe. Check filter on device + rates. Press Install, restart , close.

![N|Solid](https://lh3.googleusercontent.com/-WWuhlwyKfaw/WwFnHOKY1VI/AAAAAAAAVmo/13iLo6kUBecCL9QtZ8fTL9SN3FQCRnDKgCHMYCw/s0/Setup_2018-05-20_15-16-26.png)

## Install patch driver
We need to patch driver on every windows boot. Open task scheduler and import tasks (Actions -> Import) MouseOC_1.xml and MouseOC_2.xml
(C:\Program Files\atsiv\MouseOC_1.xml)

Edit second entry. Replace **VID_093A** with right one we found early
```sh
"C:\Program Files\atsiv\devcon.exe"
restart *VID_093A*
```
Restart PC or run this task with right click

## Test
Run extra/mouserate.exe

![N|Solid](https://lh3.googleusercontent.com/-aeDyHaLbjq0/WwFo-GyymnI/AAAAAAAAVnQ/Sh6anEgLHsgLZVnb-YAnF8K2ClCBrNCogCHMYCw/s0/mouserate_2018-05-20_15-24-21.png)

## Troubleshooting
Read original guide http://www.overclock.net/forum/375-mice/1589644-usb-mouse-hard-overclocking-2000-hz.html and use search here and there http://www.overclock.net/forum/375-mice/1597441-digitally-signed-sweetlow-1000hz-mouse-driver-78.html