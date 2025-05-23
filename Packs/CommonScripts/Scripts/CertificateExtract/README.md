Extract fields from a certificate file and return the standard context

## Script Data

---

| **Name** | **Description** |
| --- | --- |
| Script Type | python3 |
| Tags |  |
| Cortex XSOAR Version | 6.0.0 |

## Inputs

---

| **Argument Name** | **Description** |
| --- | --- |
| pem | Certificate in PEM format |
| entry_id | Certificate entry ID \(in DER or PEM format\) |

## Outputs

---

| **Path** | **Description** | **Type** |
| --- | --- | --- |
| Certificate.Name | Name \(CN or SAN\) appearing in the certificate. | String |
| Certificate.SubjectDN | The Subject Distinguished Name of the certificate.<br/>This field includes the Common Name of the certificate.<br/> | String |
| Certificate.PEM | Certificate in PEM format. | String |
| Certificate.IssuerDN | The Issuer Distinguished Name of the certificate. | String |
| Certificate.SerialNumber | The Serial Number of the certificate. | String |
| Certificate.ValidityNotAfter | End of certificate validity period. | Date |
| Certificate.ValidityNotBefore | Start of certificate validity period. | Date |
| Certificate.SubjectAlternativeName.Type | Type of the SAN. | String |
| Certificate.SubjectAlternativeName.Value | Name of the SAN. | String |
| Certificate.SHA512 | SHA512 Fingerprint of the certificate in DER format. | String |
| Certificate.SHA256 | SHA256 Fingerprint of the certificate in DER format. | String |
| Certificate.SHA1 | SHA1 Fingerprint of the certificate in DER format. | String |
| Certificate.MD5 | MD5 Fingerprint of the certificate in DER format. | String |
| Certificate.PublicKey.Algorithm | Algorithm used for public key of the certificate. | String |
| Certificate.PublicKey.Length | Length in bits of the public key of the certificate. | Number |
| Certificate.PublicKey.Modulus | Modulus of the public key for RSA keys. | String |
| Certificate.PublicKey.Exponent | Exponent of the public key for RSA keys. | Number |
| Certificate.PublicKey.PublicKey | The public key for DSA/Unknown keys. | String |
| Certificate.PublicKey.P | The P parameter for DSA keys. | String |
| Certificate.PublicKey.Q | The Q parameter for DSA keys. | String |
| Certificate.PublicKey.G | The G parameter for DSA keys. | String |
| Certificate.PublicKey.X | The X parameter for EC keys. | String |
| Certificate.PublicKey.Y | The Y parameter for EC keys. | String |
| Certificate.PublicKey.Curve | Curve of the Public Key for EC keys. | String |
| Certificate.SPKISHA256 | SHA256 fingerprint of the certificate Subject Public Key Info. | String |
| Certificate.Signature.Algorithm | Algorithm used in the signature of the certificate. | String |
| Certificate.Signature.Signature | Signature of the certificate. | String |
| Certificate.Extension.Critical | Critical flag of the certificate extension. | Bool |
| Certificate.Extension.OID | OID of the certificate extension. | String |
| Certificate.Extension.Name | Name of the certificate extension. | String |
| Certificate.Extension.Value | Value of the certificate extension. | Unknown |
| Certificate.Malicious.Vendor | The vendor that reported the file as malicious. | String |
| Certificate.Malicious.Description | A description explaining why the file was determined to be malicious. | String |
| DBotScore.Indicator | The indicator that was tested. | String |
| DBotScore.Type | The indicator type. | String |
| DBotScore.Vendor | The vendor used to calculate the score. | String |
| DBotScore.Score | The actual score. | Number |

## Script Example

```!CertificateExtract entry_id="978@5b925e3c-6ab8-4209-86bf-10f4ed6a9dc0"```

## Context Example

```json
{
    "Certificate": {
        "Extension": [
            {
                "Critical": true,
                "Name": "basicConstraints",
                "OID": "2.5.29.19",
                "Value": {
                    "CA": false
                }
            },
            {
                "Critical": false,
                "Name": "subjectKeyIdentifier",
                "OID": "2.5.29.14",
                "Value": {
                    "Digest": "3fe12ea63b9cf8414f0b001f2efa8ac5bd0fc73c"
                }
            },
            {
                "Critical": false,
                "Name": "keyUsage",
                "OID": "2.5.29.15",
                "Value": {
                    "DataEncipherment": true,
                    "DigitalSignature": true,
                    "KeyAgreement": true,
                    "KeyEncipherment": true
                }
            },
            {
                "Critical": false,
                "Name": "extendedKeyUsage",
                "OID": "2.5.29.37",
                "Value": {
                    "Usages": [
                        "clientAuth"
                    ]
                }
            },
            {
                "Critical": false,
                "Name": "subjectAltName",
                "OID": "2.5.29.17",
                "Value": [
                    {
                        "Type": "dNSName",
                        "Value": "*.example.com"
                    }
                ]
            }
        ],
        "IssuerDN": "CN=TestCA,OU=CA,O=Example.com,L=Casacca,ST=PR,C=IT",
        "MD5": "ac2fead0b8ac25a3633194b38ad91ca9",
        "Name": [
            "*.example.com",
            "IAmADVCertificate"
        ],
        "PEM": "-----BEGIN CERTIFICATE-----\nMIIDzjCCAbagAwIBAgIIXAVHw/CcpwowDQYJKoZIhvcNAQELBQAwYDELMAkGA1UE\nBhMCSVQxCzAJBgNVBAgTAlBSMRAwDgYDVQQHEwdDYXNhY2NhMRQwEgYDVQQKEwtF\neGFtcGxlLmNvbTELMAkGA1UECxMCQ0ExDzANBgNVBAMTBlRlc3RDQTAeFw0yNjEy\nMDIxNDQxMDBaFw0yMTEyMDIxNDQxMDBaMBwxGjAYBgNVBAMTEUlBbUFEVkNlcnRp\nZmljYXRlMHYwEAYHKoZIzj0CAQYFK4EEACIDYgAEfWq17YxZZuf/jPU/to3HRumn\nv8/LgZQSwkKUNdXs6niQYplCHTGQW1g062EtrhDhrWXYDIR1wxxt139y+z3hs9KP\ngThaIkJNjFx8dVklvIWx16c6t4cujZSVr6/08TLOo34wfDAMBgNVHRMBAf8EAjAA\nMB0GA1UdDgQWBBQ/4S6mO5z4QU8LAB8u+orFvQ/HPDALBgNVHQ8EBAMCA7gwEwYD\nVR0lBAwwCgYIKwYBBQUHAwIwGAYDVR0RBBEwD4INKi5leGFtcGxlLmNvbTARBglg\nhkgBhvhCAQEEBAMCBaAwDQYJKoZIhvcNAQELBQADggIBAAEhwtW+srmNaTs1krrt\nxybcF23jDNzRv/2G91PHf0CxFq7BjHYYzF3CvvwaQfTXMKog6j5arenuKgLEPpO9\navXiAcPt7vy3bxqX8WP4xgjoaRcEglS0cwW7bc+wtQT2NzqCsiXqNeRSiHXanNLY\nBGOayOnulnWP9vuAHNhgTDgxvMphxNDYtY9MA1Qj+Bs0jIuRHdFWBTVXvPYaMr4/\nbtzhrJY7VeS47IXDyp9KZbczy+5LUSh7AdKjXOI/kG8MUlKvfw/Vy23rDIOwb/dM\n/PWnqkbTFZI6cBl5FxWh2i/MaYUvjaynS/6A1fZIsgnq9mcCO/Auzaw8pa4Zx55w\nnf5hHBtp/Ksc+0ayPgYmfYKNGYvu/DQW3gvMAigYYaLAIrykYbkDl7mmQgL9lBIT\nBpBN72+ho1oZWb7F8YrbPa4odu2PBxO8kuleQKMfW73rQVF9BWUoxk8oDdHFkeye\nA+saBni5EZyYyLDMJRB2R9h/6mC02JkCRceHf7STNxiTvHwew8eP7mTNfmyTJDND\nEsGgwQpK6w0ki3/kQ3pD8rFUtpnA3AqjB0BON6j+lSpyPx/2HvGSvSx3aT2B6apC\nnoZV/cVfp9txXt1CkRt3zLpdzbQWTrRUiL+L2EaLeHPd901NZG0voxVUP64TuouB\nSIzBSFl5/q4tqkY4D2Gv4gPX\n-----END CERTIFICATE-----\n",
        "PublicKey": {
            "Algorithm": "EC",
            "Curve": "secp384r1",
            "Length": 384,
            "X": "7d:6a:b5:ed:8c:59:66:e7:ff:8c:f5:3f:b6:8d:c7:46:e9:a7:bf:cf:cb:81:94:12:c2:42:94:35:d5:ec:ea:78:90:62:99:42:1d:31:90:5b:58:34:eb:61:2d:ae:10:e1",
            "Y": "ad:65:d8:0c:84:75:c3:1c:6d:d7:7f:72:fb:3d:e1:b3:d2:8f:81:38:5a:22:42:4d:8c:5c:7c:75:59:25:bc:85:b1:d7:a7:3a:b7:87:2e:8d:94:95:af:af:f4:f1:32:ce"
        },
        "SHA1": "18ac1daece43f5b769260adbabf763046ebda80e",
        "SHA256": "869c151a7174f95a35b58c7aa900da5daed3723b63a31f08b89edd788653e402",
        "SPKISHA256": "f2d670d5c0e7e3ba2fb928dc2533c0191a679170acd7dc9387130173492e4b18",
        "SerialNumber": "6630784933253916426",
        "Signature": {
            "Algorithm": "sha256",
            "Signature": "0121c2d5beb2b98d693b3592baedc726dc176de30cdcd1bffd86f753c77f40b116aec18c7618cc5dc2befc1a41f4d730aa20ea3e5aade9ee2a02c43e93bd6af5e201c3edeefcb76f1a97f163f8c608e86917048254b47305bb6dcfb0b504f6373a82b225ea35e4528875da9cd2d804639ac8e9ee96758ff6fb801cd8604c3831bcca61c4d0d8b58f4c035423f81b348c8b911dd156053557bcf61a32be3f6edce1ac963b55e4b8ec85c3ca9f4a65b733cbee4b51287b01d2a35ce23f906f0c5252af7f0fd5cb6deb0c83b06ff74cfcf5a7aa46d315923a7019791715a1da2fcc69852f8daca74bfe80d5f648b209eaf667023bf02ecdac3ca5ae19c79e709dfe611c1b69fcab1cfb46b23e06267d828d198beefc3416de0bcc02281861a2c022bca461b90397b9a64202fd94121306904def6fa1a35a1959bec5f18adb3dae2876ed8f0713bc92e95e40a31f5bbdeb41517d056528c64f280dd1c591ec9e03eb1a0678b9119c98c8b0cc25107647d87fea60b4d8990245c7877fb493371893bc7c1ec3c78fee64cd7e6c9324334312c1a0c10a4aeb0d248b7fe4437a43f2b154b699c0dc0aa307404e37a8fe952a723f1ff61ef192bd2c77693d81e9aa429e8655fdc55fa7db715edd42911b77ccba5dcdb4164eb45488bf8bd8468b7873ddf74d4d646d2fa315543fae13ba8b81488cc1485979feae2daa46380f61afe203d7"
        },
        "SubjectAlternativeName": [
            {
                "Type": "dNSName",
                "Value": "*.example.com"
            }
        ],
        "SubjectDN": "CN=IAmADVCertificate",
        "ValidityNotAfter": "2021-12-02T14:41:00.000Z",
        "ValidityNotBefore": "2026-12-02T14:41:00.000Z"
    },
    "DBotScore": {
        "Indicator": "869c151a7174f95a35b58c7aa900da5daed3723b63a31f08b89edd788653e402",
        "Score": 0,
        "Type": "certificate",
        "Vendor": "X509Certificate"
    }
}
```

## Human Readable Output

>Certificate decoded
