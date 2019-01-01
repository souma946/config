# Let's Encryptの作成方法
certbotでstandaloneモードで作成するときの手順

## 必要なもののインストール(CentOS7)
```shell
yum install -y epel-release
yum install -y certbot
```

## 作成
```shell
certbot certonly --manual --preferred-challenges=dns -d <証明書を作成したいFQDN> -m <mail address>
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator manual, Installer None
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org
Obtaining a new certificate
Performing the following challenges:
dns-01 challenge for test1.k8s.946soma.xyz

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
NOTE: The IP of this machine will be publicly logged as having requested this
certificate. If you're running certbot in manual mode on a machine that is not
your server, please ensure you're okay with that.

Are you OK with your IP being logged?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: y
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please deploy a DNS TXT record under the name
_acme-challenge.<証明書を作成したいFQDN> with the following value:

Ys6EbrmGl-IJWQb9jaT8RgV3Yqt0l3H5Z1y61iBcH48

Before continuing, verify the record is deployed.
```

* DNSのTXTレコードに_acme-challenge.<証明書を作成したいFQDN>を登録する
* VALUEはYs6EbrmGl-IJWQb9jaT8RgV3Yqt0l3H5Z1y61iBcH48を設定する　
* この値はcertbotを実行する都度変わる

```shell
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Press Enter to Continue
Waiting for verification...
Resetting dropped connection: acme-v02.api.letsencrypt.org
Resetting dropped connection: acme-v02.api.letsencrypt.org
Cleaning up challenges
Resetting dropped connection: acme-v02.api.letsencrypt.org

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/<証明書を作成したいFQDN>/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/<証明書を作成したいFQDN>/privkey.pem
   Your cert will expire on 2019-04-01. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot
   again. To non-interactively renew *all* of your certificates, run
   "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le

```
