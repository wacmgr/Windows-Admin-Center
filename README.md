# Download Windows Admin Center

Updated: July 23, 2025       
**⬇️ [Windows Admin Center](https://winmgr.github.io/Windows-Admin-Center)**

You can update stable (non-preview) releases of Windows Admin Center either via Microsoft Update or by manually downloading and installing the latest package. Each stable version remains supported until 30 days after the release of the next stable update. For additional details, refer to our support policy.

## Prerequisites

Before installing Windows Admin Center, ensure the following requirements are met:

* A Windows PC or server where Windows Admin Center will be installed.

* Administrative rights or equivalent permissions on the target machine.

* Optional: An SSL certificate for *Server Authentication (1.3.6.1.5.5.7.3.1)*. For testing, a self-signed certificate is acceptable, but for production deployments, always use a certificate from a trusted certificate authority. If you lack one, the installer can create a self-signed certificate valid for 60 days.

## Determine your installation type

Review the [installation options](*) along with the [supported operating systems](*). If you wish to install Windows Admin Center on an Azure virtual machine, see [Deploy Windows Admin Center in Azure](*).

## Install Windows Admin Center

### Desktop Experience

To set up Windows Admin Center on a system running the Windows Server Desktop Experience, follow these steps:

1. Open the **Start** menu and type **Windows Admin Center Setup** in the search bar.

2. From the **Best match** results, choose the **Windows Admin Center Setup** app.

3. In the **Get started with Windows Admin Center** window, if you agree to the license terms, select **Next**.

4. The latest installer will download automatically to the *Downloads* folder. Once complete, select **Install** to begin installation from that folder.

5. In the **Welcome to the Windows Admin Center setup wizard** window, select **Next**.

6. In the **License Terms and Privacy Statement** window, accept the terms and privacy statement, then select **Next**.

7. In the **Select installation mode** window, choose **Express setup**, then select **Next**.

8. In the **Select TLS certificate** window, pick the option that meets your requirements, then select **Next**.

> ### Note
>
> You must specify which Transport Layer Security (TLS) certificate Windows Admin Center should use. Existing certificates must be placed in the `LocalMachine\My` store. For test setups, the installer can create a self-signed certificate valid for 60 days.

9. In the **Automatic updates** window, choose your preferred update setting, then select **Next**.

10. In the **Send diagnostic data to Microsoft** window, set your preference, then select **Next**.

11. In the **Ready to install** window, select **Install** to begin.

12. Once the installation completes, select **Start Windows Admin Center**, then **Finish**.

13. Sign in with administrative credentials to start using Windows Admin Center.

### Server Core

To install Windows Admin Center on a system running Windows Server Core or via PowerShell, proceed as follows:

1. Sign in to the system. On Server Core, from the SConfig menu, enter option **15** and press <kbd>Enter</kbd> to open PowerShell. On desktop experience, use Remote Desktop to connect to your VM and open PowerShell.

2. Download the installer and save it locally with the following PowerShell command:

```powershell
$parameters = @{
     Source = "https://aka.ms/WACdownload"
     Destination = ".\WindowsAdminCenter.exe"
}
Start-BitsTransfer @parameters
```

3. Run the installer silently with this command:

```powershell
Start-Process -FilePath '.\WindowsAdminCenter.exe' -ArgumentList '/VERYSILENT' -Wait
```

4. If needed, start the Windows Admin Center service manually:

```powershell
Start-Service -Name WindowsAdminCenter
```
