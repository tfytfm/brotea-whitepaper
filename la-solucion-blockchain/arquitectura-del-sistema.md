# Arquitectura del Sistema

La plataforma FutureHands se compone de los siguientes elementos clave:

* **Frontend (Flutter):** Interfaces web y móvil intuitivas para donantes y beneficiarios.
* **Backend (Node.js, Express.js):** Gestiona la lógica de la aplicación y la comunicación con la blockchain.
* **API (RESTful):** Permite la interacción entre el frontend y el backend.
* **Smart Contracts (Solidity, Hardhat):** Automatizan la gestión de donaciones, la distribución de fondos y la lógica de la plataforma.
* **Blockchain (Polygon):** Registra las transacciones de forma segura, transparente e inmutable.
* **Almacenamiento (IPFS, PostgreSQL):** Almacena información de manera descentralizada (IPFS) y datos no transaccionales (PostgreSQL).
* **Servicios de Terceros:** Integración con servicios de KYC/AML y oráculos (Chainlink).

```mermaid
graph LR
    subgraph Clientes
        Donante[Donante App]
        Beneficiario[Beneficiario App]
        Fundación[Fundación FutureHands Admin Panel]
    end

    subgraph Capa de Aplicación
        WebApp["Interfaz Web (Flutter)"]
        MobileApp["Aplicación Móvil (Flutter)"]
        API["API (Node.js/Express.js)"]
    end

    subgraph "Capa Blockchain (Polygon)"
        SmartContracts["Smart Contracts (Solidity)"]
        NodosPolygon[Nodos Polygon]
        IPFS[Almacenamiento IPFS]
    end

    Donante --> MobileApp
    Beneficiario --> MobileApp
    Fundación --> WebApp

    WebApp --> API
    MobileApp --> API
    API --> SmartContracts
    SmartContracts --> NodosPolygon
    SmartContracts <--> IPFS


    style SmartContracts fill:#ccf,stroke:#888,stroke-width:2px
    style NodosPolygon fill:#ccf,stroke:#888,stroke-width:2px
    style IPFS fill:#ccf,stroke:#888,stroke-width:2px

```
