# Hyper-V Gallery

This project extends the official Hyper-V Quick Create Gallery with additional official Hyper-V images provided by Linux vendors.

This is a continuation of an [earlier project](https://github.com/sirredbeard/legacy-hyper-v-gallery) created for a [blog post](https://boxofcables.dev/hyper-v-gallery/). That project contained generic .ISO images from various Linux distributions. **This project only contains official Hyper-V images provided by Linux vendors.**

## Installation

### tl;dr: open PowerShell as Administrator and run
```
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\"  `
    -Name 'GalleryLocations' -PropertyType MultiString -Value (
    'https://raw.githubusercontent.com/sirredbeard/hypervgallery/master/gallery.json',
    'https://go.microsoft.com/fwlink/?linkid=851584')
$newValue.multistring
```
This adds the gallery json from this repository alongside the existing Microsoft gallery json.

### Use the included PowerShell Script: add_gallery.ps1

* Download add_gallery.ps1
* If you have not done so already, enable PowerShell scripts by opening PowerShell as admin and running: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser``
* Make sure you are admin, cd to the folder with add_gallery.ps1, and run it: ``.\add_gallery.ps1`

## Uninstalltion

###
```
Remove-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\" -Name "GalleryLocations"
```
### Use the included PowerShell Script: rm_gallery.ps1

* Download rm_gallery.ps1
* If you have not done so already, enable PowerShell scripts by opening powershell as admin and running: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser``
* Make sure you are admin, cd to the folder with rm_gallery.ps1, and run it: `.\rm_gallery.ps1`

## Credits

This project was inspired by the following:

"[How to create a Custom Hyper-V Quick Create VM Gallery](https://techcommunity.microsoft.com/t5/ITOps-Talk-Blog/How-to-create-a-Custom-Hyper-V-Quick-Create-VM-Gallery/ba-p/781346)" by Thomas Maurer
"[Create a custom virtual machine gallery](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/user-guide/custom-gallery?WT.mc_id=itopstalk-blog-thmaure)" by Sarah Cooley
"[Create your custom Quick Create VM gallery](https://techcommunity.microsoft.com/t5/Virtualization/Create-your-custom-Quick-Create-VM-gallery/ba-p/382388)" by Lars Iwer