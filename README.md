# Warmlink Heat Pump Dashboard for Home Assistant

Dashboard Lovelace dla pomp ciepła Warmlink/Phinx z integracją [warmlink-ha](https://github.com/warsztatroch-droid/warmlink-ha).

## Wymagania

- Home Assistant
- Zainstalowana integracja [Warmlink](https://github.com/warsztatroch-droid/warmlink-ha)

## Instalacja

### 1. Znajdź swój DEVICE_CODE

1. Idź do **Settings → Devices & Services → Warmlink**
2. Kliknij na swoje urządzenie
3. Zobacz ID encji, np. `sensor.warmlink_abc123def_t01`
4. Twój DEVICE_CODE to: `abc123def`

### 2. Dodaj dashboard

**Opcja A - Nowy dashboard:**

1. **Settings → Dashboards → Add Dashboard**
2. Nazwij np. "Pompa Ciepła"
3. Otwórz nowy dashboard
4. **⋮ → Edit Dashboard → ⋮ → Raw configuration editor**
5. Wklej zawartość `dashboard.yaml`
6. Zamień wszystkie `DEVICE_CODE` na swój kod
7. Zapisz

**Opcja B - Dodaj do istniejącego:**

1. Otwórz dashboard → **⋮ → Edit Dashboard**
2. **+ Add Card → Manual**
3. Wklej pojedyncze karty z pliku `cards/`

## Struktura

```
├── dashboard.yaml          # Kompletny dashboard (3 zakładki)
├── cards/
│   ├── status.yaml         # Karta statusu
│   ├── thermostat.yaml     # Termostat
│   ├── temperatures.yaml   # Wskaźniki temperatur
│   ├── switches.yaml       # Przełączniki
│   ├── selects.yaml        # Wybory trybu
│   ├── setpoints.yaml      # Suwaki temperatur
│   ├── performance.yaml    # Wydajność (COP, moc)
│   └── charts.yaml         # Wykresy historii
└── automations/
    └── examples.yaml       # Przykładowe automatyzacje
```

## Screenshot

![Dashboard Preview](docs/dashboard-preview.png)

## Encje

### Przełączniki (Switch)

| Entity ID                                  | Opis                 |
| ------------------------------------------ | -------------------- |
| `switch.warmlink_DEVICE_CODE_power_switch` | Zasilanie            |
| `switch.warmlink_DEVICE_CODE_h22_switch`   | Tryb cichy           |
| `switch.warmlink_DEVICE_CODE_h05_switch`   | Funkcja chłodzenia   |
| `switch.warmlink_DEVICE_CODE_g05_switch`   | Dezynfekcja          |
| `switch.warmlink_DEVICE_CODE_h01_switch`   | Pamięć po wyłączeniu |

### Wybory (Select)

| Entity ID                                 | Opis                    |
| ----------------------------------------- | ----------------------- |
| `select.warmlink_DEVICE_CODE_mode_select` | Tryb pracy              |
| `select.warmlink_DEVICE_CODE_h07_select`  | Tryb sterowania         |
| `select.warmlink_DEVICE_CODE_h21_select`  | Jednostka temperatury   |
| `select.warmlink_DEVICE_CODE_h25_select`  | Źródło sterowania temp. |

### Suwaki (Number)

| Entity ID                         | Opis             | Zakres  |
| --------------------------------- | ---------------- | ------- |
| `number.warmlink_DEVICE_CODE_r01` | Temp. CWU        | 20-65°C |
| `number.warmlink_DEVICE_CODE_r02` | Temp. ogrzewania | 20-65°C |
| `number.warmlink_DEVICE_CODE_r03` | Temp. chłodzenia | 7-25°C  |
| `number.warmlink_DEVICE_CODE_r70` | Temp. pokojowa   | 5-27°C  |

### Sensory temperatury

| Entity ID                         | Opis                    |
| --------------------------------- | ----------------------- |
| `sensor.warmlink_DEVICE_CODE_t01` | Woda wlotowa            |
| `sensor.warmlink_DEVICE_CODE_t02` | Woda wylotowa           |
| `sensor.warmlink_DEVICE_CODE_t04` | Zewnętrzna              |
| `sensor.warmlink_DEVICE_CODE_t08` | Zasobnik CWU            |
| `sensor.warmlink_DEVICE_CODE_t30` | Częstotliwość sprężarki |

## Licencja

MIT
