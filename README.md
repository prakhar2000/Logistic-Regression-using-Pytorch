```mermaid
flowchart TD
    A[Ant and bee images] --> B[Train and validation splits]
    B --> C[Training transforms<br/>random crop and flip]
    B --> D[Validation transforms<br/>resize and center crop]
    C --> E[Tensor conversion and normalization]
    D --> E
    E --> F[DataLoader batches]

    F --> G[Flatten each image]
    G --> H[Linear score<br/>z = xW + b]
    H --> I[Logit]
    I --> J[Sigmoid]
    J --> K[Probability of bee]
    K --> L[Threshold at 0.5<br/>ant or bee]

    I --> M[BCEWithLogitsLoss]
    F --> N[True labels]
    N --> M
    M --> O[Backpropagation]
    O --> P[Adam optimizer updates W and b]
    P --> H

    L --> Q[Validation predictions]
    Q --> R[Validation accuracy]
