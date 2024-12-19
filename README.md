# iot22_cloud_actionsdemo

För att skapa azure-credentials för GitHub actions:

Skriv först: (Ersätt "flasktest" med ditt resursnamn från Azure)
```console
az group show --name flasktest --query id --output tsv
```

Kopiera texten som skrivs ut in till detta kommando: (Återigen, ersätt "flasktest")
```console
az ad sp create-for-rbac --name flasktest --role contributor --scope KLISTRA_IN_HÄR --sdk-auth
```

Detta kommando ger er en lång text i stil med:
```json
{
  "clientId": "<GUID>",
  "clientSecret": "<GUID>",
  "subscriptionId": "<GUID>",
  "tenantId": "<GUID>",
  (...)
}
```

Kopiera hela detta block och spara det i en ny hemlighet i GitHub-repot som heter `AZURE_CREDENTIALS`