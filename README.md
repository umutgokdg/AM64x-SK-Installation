# AM64X-SK 


## 1-	SDK and Tools Setup

### 1.1- SDK
Bir "Texas Instruments" hesabı açarak verilen bağlantıdan "SDK"nın 08.06.00.45 versiyonunu _**C:/ti**_ dizinine indirin: 
_https://www.ti.com/tool/download/MCU-PLUS-SDK-AM64X/08.06.00.45_

### 1.2- SysConfig
Verilen bağlantıdan "SysConfig 1.14.0" uygulamasını _**C:/ti**_ dizinine indirin:
_https://software-dl.ti.com/ccs/esd/sysconfig/sysconfig-1.14.0_2667-setup.exe_

"SysConfig" indirme ana sayfası ve diğer versiyonlar : _https://www.ti.com/tool/SYSCONFIG_

### 1.3- GCC AARCH64 Compiler 
Verilen bağlantıdan "GCC AARCH64 Compiler" uygulamasını _**C:/ti**_ dizinine indirin:
_https://developer.arm.com/-/media/Files/downloads/gnu-a/9.2-2019.12/binrel/gcc-arm-9.2-2019.12-mingw-w64-i686-aarch64-none-elf.tar.xz_

### 1.4- GCC ARM (R5) Compiler
Verilen bağlantıdan "GCC ARM (R5) Compiler" uygulamasını _**C:/ti**_ dizinine indirin:
_https://developer.arm.com/-/media/Files/downloads/gnu-rm/7-2017q4/gcc-arm-none-eabi-7-2017-q4-major-win32.zip_

### 1.5- Python3 
Verilen bağlantıdan "Python 3.9.1" indirin. "Python" sürümünün **3.9.1** olmasına dikkat edin:
_https://www.python.org/downloads/windows/_

"Python" indikten sonra doğru versiyonu kurduğunuzu komut satırından aşağıdaki komut ile kontrol edin:
```
$ C:\Users\PC_4423>python --version

Python 3.9.1
``` 

"Windows"un indirdiğiniz "Python" sürümünü gördüğüne emin olmak için "Environment Variables"ta şu "path"in olduğunu doğrulayın, yoksa yeni "path" olarak ekleyin:  _**C:\Users\\{your_username}\AppData\Local\Programs\Python\Python39**_

"Python package manager(pip)"in yüklü olduğunu aşağıdaki komut ile kontrol edin:
```
$ C:\Users\PC_4423>python -m pip –version

pip 20.2.3 from C:\Users\PC_4423\AppData\Local\Programs\Python\Python39\lib\site-packages\pip (python 3.9)
```

Arkasından yine komut satırında aşağıdaki komutu çalıştırarak ek paketleri yükleyin:
```
$ C:\Users\PC_4423>python -m pip install pyserial xmodem tqdm
```
### 1.6 OpenSSL
Verilen bağlantıdan "OpenSSL v1.1.1"i indirin:
_https://slproweb.com/products/Win32OpenSSL.html_

Kurulumu "default" dizine yapın: _**C:/Program Files/OpenSSL-Win64/**_

"Binary" dosyaları indirmek için gelen seçenekte _**/bin**_ dosyasına indirmeyi seçin, "Windows system path"ine değil.

"Environment Variables"a şu "path"i ekleyin: _**C:/Program Files/OpenSSL-Win64/bin**_

Doğru versiyonu indirdiğinize komut satırında aşağıdaki komutu çalıştırarak emin olun:
```
$ C:\Users\PC_4423>openssl version

OpenSSL 1.1.1v  1 Aug 2023
```

### 1.7 PRU-CGT
Verilen bağlantıdan "PRU-CGT-2.3.1"i _**C:/ti/**_ dizinine indirin:
_https://www.ti.com/tool/download/PRU-CGT_

### 1.8 TI CLANG Compiler Toolchain
Verilen bağlantıdan "Clang"i _**C:/ti/**_ dizinine indirin:
_https://dr-download.ti.com/software-development/ide-configuration-compiler-or-debugger/MD-ayxs93eZNN/2.1.2.LTS/ti_cgt_armllvm_2.1.2.LTS_windows-x64_installer.exe_


## 2-	CCS Setup

### 2.1 Download CCS
Verilen bağlantıdan "CCS 12.1.0 zip"ini yükleyin ve herhangi bir yere ayıklayın:
_https://www.ti.com/tool/download/CCSTUDIO_

### 2.2 Install CCS
Ayıklanan dosyaların içinden ".exe" uzantılı dosyayı çalıştırın.

"Installation Directory" olarak _**C:\ti\ccs1210**_ dizinini seçin.
"Setup Type" olarak "Custom Installation"ı seçin.

"Select Components" kısmından “Sitara AM3x, AM4x, AM5x and AM6x MPUs” kutucuğunu işaretleyin. 

<center>
<img src="images\figure4.png" width="900">
</center>
 
"CCS" kurulumu bitinceye kadar kalan steplerde bir değişiklik yapmayın ve kurulum bittikten sonra "CCS"i çalıştırın. 

"Select a directory as workspace" kısmına _**C:\Users\\{username}\workspace_v11**_ yazarak "workspace"inizi oluşturun.

### 2.3- Check packages as seen by CCS
"CCS" açıldıktan sonra üst kısımda görünen "_window>preferences_"a gidin.

Arkasından "_Code Composer Studio>Products_"a gidin ve "SysConfig1.14.0"ı görebilidiğinize emin olun.

<center>
<img src="images\figure5.png" width="900">
</center>

"_Code Composer Studio>Build>Compilers_"a gidin ve "TI Clang v2.1.2.LTS"i gördüğünüze emin olun.

<center>
<img src="images\figure6.png" width="900">
</center>

### 2.4 Create Target Configuration
"_View>Target Configurations_"a gidin, gelen pencereden "User Defined"a sağ tıklayarak "New target Configuration"ı seçin.

<center>
<img src="images\figure7.png" width="500">
</center>

Ve güzel bir isim verin.

<center>
<img src="images\figure8.png" width="700">
</center>
 
Aşağıdaki adımlardaki seçenekleri sırasıyla seçin:
 
<center>
<img src="images\figure9.png" width="600">
</center>

<center>
<img src="images\figure10.png" width="600" >
</center>

Aşağıdaki adımı yapabilmek için bir önceki görsel ile aynı penceredeyken alt tarafta görünen "advanced" penceresine gidin ve görseldeki gibi "bypassed" şeklinde işaretlenmiş tüm seçenekleri sırayla seçip şekildeki gibi "bypass" kutucuğunu işaretleyin:

<center>
<img src="images\figure11.png" width="700">
</center>

İşlemler bittikten sonra hem "advanced" hem de "basic" penceresinde "save" kutucuğuna basın.


## 3-   SK Setup


<center>
<img src="images\figure12.png" width="900">
</center>
 
"Power Supply" soketi bağlı ve "Off/On switch" kapalı iken 1, açık içen 2 yeşil ışık yanmalıdır.
"JTAG" ve "UART" portları için de bağlanıldığı zaman 1 yeşil ışık yanmalıdır.
 
"UART to USB" portuna bağlandığını zaman cihazınız aygıt yöneticisinde şunu görmeniz gerekir.

<center>
<img src="images\figure13.png" width="900">
</center>
 
"COM" numaraları değişken olabilir.
Eğer "UART to USB" bağlantıları burada görünmüyorsa verilen bağlantı üzerinden bir "UART to USB driver"ı kurmanız gerekir: 
_https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers_

### 3.1- Opening a Terminal
"_View>Terminal_"e gidin ve şekildeki kutucuğa basarak yeni terminal açın:

<center>
<img src="images\figure14.png" width="900">
</center>

<center>
<img src="images\figure15.png" width="500">
</center>
 
Ayarları şekildeki gibi seçin, "Serial port" numarasını aygıt yöneticisinden "Standard COM Port" numarası olarak ayarlayın.


## 4-	Flash SOC Initialization Binary
Öncelikle "UART" portuna bağlı ve terminal açıkken "AM64x-SK"nın gücünü kesin.
Belirtilinceye kadar hiçbir kablonun sökülmemesi ve "power switch"in değiştirilmemesi büyük önem arz etmektedir.

Güç kesme ve güç verme işlemlerini "power switch" ile yapınız.
"SW2" ve "SW3" kısmındaki "switch"leri "UART boot" moduna getirin:

<center>
<img src="images\figure16.png" width="600">
</center>
 
"AM64x-SK"ya tekrardan güç verdiğinizde açık olan terminalde şu mesajın basılı olduğunu ve her 2-3 saniyede bir “C” harfinin basıldığını göreceksiniz:

<center>
<img src="images\figure17.png" width="900">
</center>
 
Üstteki şekilde okla gösterilen tuşa basarak terminali kapatın.
Yönetici olarak komut satırını çalıştırın ve sırasıyla şu komutları girin:

<center>
<img src="images\figure18.png" width="900">
</center>
 
Komuttaki "COM" numarasını kendi bilgisayarınızdaki numaraya göre değiştirip girmeyi unutmayın.

Şimdi hem komut satırını hem de "CCS" üstündeki terminali kapatıp "AM64x-SK"nın gücünü kesin.

Aynı porta bağlanan yeni bir terminal açın ve "SW2" ve "SW3" kısmındaki "switch"leri "OSPI" boot moduna getirin:

<center>
<img src="images\figure19.png" width="600">
</center>
 
"AM64x-SK"ya tekrardan güç verdiğinizde açık olan terminalde şu mesajın basılı olduğunu göreceksiniz:

<center>
<img src="images\figure20.png" width="900">
</center>

Bu işlemleri başarılı bir şekilde yaptığınızda "AM64x-SK"nın kurulumu için **bir** kez yapmanız gereken adımları tamamlamış bulunuyorsunuz.

Artık verilen bağlantıyla bir “Hello World” projesi inşa edip çalıştırabilirsiniz:
_file:///C:/ti/mcu_plus_sdk_am64x_08_06_00_45/docs/api_guide_am64x/GETTING_STARTED_BUILD.html_

Bağlantıyı kendi bilgisayarınızdaki "path"e göre güncellemeyi unutmayın.

Eğer işlemleri yaparken hata alıyorsanız tüm adımları baştan yapabilir ve indirdiğiniz uygulamaların versiyonlarının birebir aynı olduğuna emin olabilirsiniz.
