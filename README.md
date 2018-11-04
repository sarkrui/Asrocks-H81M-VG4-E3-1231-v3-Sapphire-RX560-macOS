# Asrocks-H81M-VG4-E3-1231-v3-Sapphire-RX460-High-Sierra

![](https://i.imgur.com/CkVh4qx.jpg)

### Specs

- Asrocks H81M-VG4
- E3 1231 V3
- DDR3 1600 8G * 2
- Sapphire RX 460 4GB nitro 
- 850 EVO 250G\128G
- BCM94331CD 



### Fix Continuity
Continuity Activation Tool (CAT) aims to repair iMessage, iCloud and FaceTime.

#### Set correct BSD name

Open Terminal
> sudo rm -rf /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist into Terminal and enter password on prompt

> sudo rm -rf /Library/Preferences/SystemConfiguration/preferences.plist into Terminal
> Reboot Hackintosh and check iMessage/iCloud/Facetime

2. Bad System Preferences

  Terminal to trigger password prompt if necessary.
> sudo rm into 

Paste all at once into Terminal:
> sudo rm -rf ~/Library/Caches/com.apple.iCloudHelper* \
> ​          ~/Library/Caches/com.apple.Messages* \
> ​          ~/Library/Caches/com.apple.imfoundation.IMRemoteURLConnectionAgent* \
> ​          ~/Library/Preferences/com.apple.iChat* \
> ​          ~/Library/Preferences/com.apple.icloud* \
> ​          ~/Library/Preferences/com.apple.imagent* \
> ​          ~/Library/Preferences/com.apple.imessage* \
> ​          ~/Library/Preferences/com.apple.imservice* \
> ​          ~/Library/Preferences/com.apple.ids.service* \
> ​          ~/Library/Preferences/com.apple.madrid.plist* \
> ​          ~/Library/Preferences/com.apple.imessage.bag.plist* \
> ​          ~/Library/Preferences/com.apple.identityserviced* \
> ​          ~/Library/Preferences/com.apple.ids.service* \
> ​          ~/Library/Preferences/com.apple.security* \
> ​          ~/Library/Messages

#### Proper SMBIOS Settings 

I personally own a MacBook Pro 13, so I utilized iMessageDebug to output everything needed and added them in the SMBIOS, Rt Varibles and System Parameters for my Clover config. 

1. Therefore, **if you own a Mac**, export your serials with `fixiMessage` and please refer to `fixiMessage2Clover.pdf` under the root folder of this repository.
2. **if you don NOT own a Mac**, you may try this below. (FYI I personally have never tried, but it's reasonably worth trying.)

##### Generate an Invalid Serial Number

1. **Download** [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/) if you don’t already have it
2. **Mount** EFI partition
3. Navigate to /Volumes/EFI/**EFI/Clover/**
4. **Right-click** config.plist and open with **Clover Configurator**
5. Click **SMBIOS** on left side
6. Copy the **Serial Number**
7. Go to [checkcoverage.apple.com](checkcoverage.apple.com)
8. Paste **Serial Number**  and click **Continue**
9. If it comes back as valid you will need to generate a new serial number until you get a error or invalid serial number
10. Go back to Clover Configurator **SMBIOS** section
11. Repeat **Generate New** and **paste** to checkcoverage.apple.com until you get an **Invalid Serial Number**

##### Set Custom Board Serial Number

Now that you have your own invalid serial number you need to replace the Board Serial Number with one containing your Invalid Serial Number along with **5 random digits**. Since they can be any digits I keep the last five digits of the *Board Serial Number* and replace the **first 12 with the Serial Number**

1. Copy **Serial Number**
2. Replace the first 12 digits of **Board Serial Number** with the copied **Serial Number**

##### Set Unique UUID

1. Open **Terminal**
2. Generate a unique string by entering `uuidgen` into **Terminal**
3. Copy & Paste the generated UUID value from Terminal into **SmUUID** in Clover Configurator -> **SMBIOS**
4. **Save** config.plist
5. **Restart** Hackintosh

