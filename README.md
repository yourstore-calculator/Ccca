# Ccca
const SHIPPING_RATE = 48;
const addonPrices = {
    curtain: 26,
    net: { door: 39, folding: 18, sliding: 14 }
};

const productData = {
    "Windows": {
        "Window Double Glass Double Frame Fixed": { price: 34, cbm: 0.13, method: 'per_meter', addons: 'curtain,net' },
        "Window Double Glass Double Frame 1-Way": { price: 34, fixed_component_cost: 39, cbm: 0.13, method: 'per_meter', addons: 'curtain,net' },
        "Window Double Glass Double Frame 2-Way": { price: 34, fixed_component_cost: 58, cbm: 0.13, method: 'per_meter', addons: 'curtain,net' },
        "Window Double Glass Single Frame Fixed": { price: 26, cbm: 0.07, method: 'per_meter', addons: 'curtain,net' },
        "Window Double Glass Single Frame 1-Way": { price: 26, fixed_component_cost: 20, cbm: 0.07, method: 'per_meter', addons: 'curtain,net' },
        "Window Double Glass Single Frame 2-Way": { price: 26, fixed_component_cost: 32, cbm: 0.07, method: 'per_meter', addons: 'curtain,net' },
        "Window Single Glass Single Frame Fixed": { price: 20, cbm: 0.07, method: 'per_meter', addons: 'net' },
        "Window Single Glass Single Frame 1-Way": { price: 20, fixed_component_cost: 13, cbm: 0.07, method: 'per_meter', addons: 'net' },
        "Window Single Glass Single Frame 2-Way": { price: 20, fixed_component_cost: 17, cbm: 0.07, method: 'per_meter', addons: 'net' },
        "Sliding Windows": { price: 41, fixed_component_cost: 10, cbm: 0.13, method: 'per_meter', addons: 'curtain' },
        "Electric Windows": { price: 102, cbm: 0.13, method: 'per_meter' },
        "Skylight without Motor": { price: 56, cbm: 0.13, method: 'per_meter' },
        "Skylight with Motor": { price: 145, cbm: 0.13, method: 'per_meter' },
        "Heavy Curtain Wall": { price: 56, cbm: 0.15, method: 'per_meter' },
        "Light Curtain Wall": { price: 45, cbm: 0.15, method: 'per_meter' },
    },
    "Doors": {
        "Entrance Door - Zinc": { price: 66, cbm: 0.20, method: 'per_meter', special: 'add_10' },
        "Entrance Door - Stainless Steel": { price: 120, cbm: 0.20, method: 'per_meter', special: 'add_10' },
        "Entrance Door - Cast Aluminum": { price: 168, cbm: 0.20, method: 'per_meter', special: 'add_10' },
        "WPC Door": { price: 45, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0, special: 'wpc_width_penalty' },
        "WPC Door - with Wood": { price: 50, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0, special: 'wpc_width_penalty' },
        "WPC Door - with Soundproof Filling": { price: 60, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0, special: 'wpc_width_penalty' },
        "WPC Door - with Aluminum Frame": { price: 68, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0, special: 'wpc_width_penalty' }, // تم التعديل إلى 68
        "WPC Glass Door": { price: 55, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0, special: 'wpc_width_penalty' }, // تم إضافة هذا النوع
        "Aluminum Door": { price: 65, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0 },
        "Aluminum Door - with Wood": { price: 75, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0 },
        "Aluminum Door - Full": { price: 85, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0 },
        "Aluminum Door - Hidden": { price: 110, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0 },
        "Aluminum Door - Exterior": { price: 61, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 1.0 },
        "Bathroom Door - New Type": { price: 55, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 0.8 },
        "Bathroom Door - Old Type": { price: 45, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 0.8 },
        "Bathroom Door - Hidden Glass": { price: 65, cbm: 0.11, method: 'per_unit', std_h: 2.2, std_w: 0.8 },
    },
    "Sliding Doors": {
        "Interior Sliding Door - Glass": { price: 38, cbm: 0.15, method: 'per_meter', addons: 'curtain' },
        "Interior Sliding Door - Solid": { price: 41, cbm: 0.15, method: 'per_meter' },
        "Exterior Sliding Door - 1 Panel Open": { price: 55, cbm: 0.15, method: 'per_meter' },
        "Exterior Sliding Door - 2 Panels Open": { price: 58, cbm: 0.15, method: 'per_meter' },
        "WPC Sliding Door": { price: 61, cbm: 0.15, method: 'per_meter' },
    },
    "Folding Doors": {
        "Interior Folding Door": { price: 39, cbm: 0.15, method: 'per_meter' },
        "Exterior Folding Door": { price: 56, cbm: 0.15, method: 'per_meter' },
    },
    "Exterior Shutters": {
        "Rolling Shutter": { price: 28, cbm: 0.20, method: 'per_meter' },
    },
    "Garden Gates": {
        "Cast Aluminum Garden Gate": { price: 91, cbm: 0.20, method: 'per_meter' },
    },
    "Barriers": {
        "Stair Barrier": { price: 43, cbm: 0.05, method: 'per_meter' },
        "Bathroom Barrier": { price: 32, cbm: 0.05, method: 'per_meter' }
    }
};

const productCodes = {
    '1': "Window Double Glass Double Frame Fixed", '2': "Window Double Glass Double Frame 1-Way", '3': "Window Double Glass Double Frame 2-Way",
    '4': "Window Double Glass Single Frame Fixed", '5': "Window Double Glass Single Frame 1-Way", '6': "Window Double Glass Single Frame 2-Way",
    '7': "Window Single Glass Single Frame Fixed", '8': "Window Single Glass Single Frame 1-Way", '9': "Window Single Glass Single Frame 2-Way",
    '10': "Sliding Windows", '11': "Electric Windows", '12': "Skylight without Motor", '13': "Skylight with Motor", '14': "Heavy Curtain Wall", '15': "Light Curtain Wall",
    'D1': "Entrance Door - Zinc", 'D2': "Entrance Door - Stainless Steel", 'D3': "Entrance Door - Cast Aluminum",
    'D4': "WPC Door", 'D5': "WPC Door - with Wood", 'D6': "WPC Door - with Soundproof Filling", 'D7': "WPC Door - with Aluminum Frame",
    'D16': "WPC Glass Door", // إضافة الكود الجديد
    'D8': "Aluminum Door", 'D9': "Aluminum Door - with Wood", 'D10': "Aluminum Door - Full", 'D11': "Aluminum Door - Hidden", 'D12': "Aluminum Door - Exterior",
    'D13': "Bathroom Door - New Type", 'D14': "Bathroom Door - Old Type", 'D15': "Bathroom Door - Hidden Glass",
    'S1': "Interior Sliding Door - Glass", 'S2': "Interior Sliding Door - Solid", 'S3': "Exterior Sliding Door - 1 Panel Open", 'S4': "Exterior Sliding Door - 2 Panels Open", 'S5': "WPC Sliding Door",
    'F1': "Interior Folding Door", 'F2': "Exterior Folding Door",
    'E1': "Rolling Shutter", 'G1': "Cast Aluminum Garden Gate",
    'B1': "Stair Barrier", 'B2': "Bathroom Barrier"
};

let resultsList = [];

function initializeApp() {
    const mainCat = document.getElementById("mainCategory");
    mainCat.innerHTML = `<option value="">-- Select Category --</option>`;
    Object.keys(productData).forEach(cat => mainCat.innerHTML += `<option value="${cat}">${cat}</option>`);
    loadSubTypes();
    renderReferenceGuide();
}

function loadSubTypes() {
    const mainCatVal = document.getElementById("mainCategory").value;
    const subType = document.getElementById("subType");
    subType.innerHTML = "";
    if (mainCatVal && productData[mainCatVal]) {
        Object.keys(productData[mainCatVal]).forEach(sub => subType.innerHTML += `<option value="${sub}">${sub}</option>`);
    }
    renderAddons();
}

function renderAddons() {
    const subVal = document.getElementById("subType").value;
    const addonsHost = document.getElementById("addonsHost");
    addonsHost.innerHTML = "";
    const data = findProductData(subVal);
    if (data && data.addons) {
        const availableAddons = data.addons.split(',');
        if (availableAddons.includes('curtain')) {
            addonsHost.innerHTML += `<div><label><input type="checkbox" id="addon_curtain"> Add Curtain (+${addonPrices.curtain} OMR/m²)</label></div>`;
        }
        if (availableAddons.includes('net')) {
            addonsHost.innerHTML += `<div><label for="addon_net_type">Add Net:</label><select id="addon_net_type"><option value="">-- None --</option><option value="door">Door (+${addonPrices.net.door} per 0.5m²)</option><option value="folding">Folding (+${addonPrices.net.folding} per 0.5m²)</option><option value="sliding">Sliding (+${addonPrices.net.sliding} per 0.5m²)</option></select></div>`;
        }
    }
    setDefaultDimensions();
}

function setDefaultDimensions() {
    const subVal = document.getElementById("subType").value;
    const data = findProductData(subVal);
    if (data && data.method === 'per_unit') {
        document.getElementById("height").value = data.std_h || 2.2;
        document.getElementById("width").value = data.std_w || 1.0;
    } else {
        document.getElementById("height").value = 1;
        document.getElementById("width").value = 1;
    }
}

function findProductData(productName) {
    for (const category in productData) {
        if (productData[category][productName]) {
            return productData[category][productName];
        }
    }
    return null;
}

function findProductByCode(code) {
    const upperCode = code.toUpperCase();
    const fullName = productCodes[upperCode];
    return fullName ? { name: fullName, data: findProductData(fullName) } : null;
}

function calculateItemPrice(item) {
    const data = item.data;
    if (!data) return { unitPrice: 0, totalPrice: 0 };
    const area = item.h * item.w;
    let basePrice = 0, sizePenalty = 0, addonCost = 0, widthPenalty = 0; // إضافة widthPenalty

    if (data.method === 'per_unit') {
        basePrice = data.price || 0;
        const stdArea = (data.std_h || 0) * (data.std_w || 0);
        if (stdArea > 0 && area > stdArea) {
            sizePenalty = Math.ceil((area - stdArea) / 0.1) * 2;
        }

        // حساب غرامة العرض لأبواب WPC (باستثناء WPC Sliding Door)
        if (data.special === 'wpc_width_penalty' && item.w > 1.0) {
            const extraWidthCm = (item.w - 1.0) * 100; // تحويل الزيادة في العرض إلى سنتيمتر
            widthPenalty = extraWidthCm * 0.3; // 0.3 OMR لكل 1 سم
        }

    } else {
        basePrice = area * (data.price || 0);
    }

    if (item.selectedAddons.curtain) {
        addonCost += area * addonPrices.curtain;
    }
    if (item.selectedAddons.netType && addonPrices.net[item.selectedAddons.netType]) {
        addonCost += (area * 0.5) * addonPrices.net[item.selectedAddons.netType];
    }

    const fixedCost = data.fixed_component_cost || 0;
    const specialCost = data.special === 'add_10' ? 10 : 0;
    const shippingCost = area * (data.cbm || 0) * SHIPPING_RATE;

    // تضمين widthPenalty في السعر الكلي للوحدة
    const unitPrice = basePrice + sizePenalty + fixedCost + specialCost + shippingCost + addonCost + widthPenalty;
    return { unitPrice, totalPrice: unitPrice * item.qty };
}

function addItem(manualData = null) {
    let newItem;
    if (manualData) {
        newItem = {
            id: Date.now(),
            name: manualData.name,
            qty: manualData.qty,
            h: manualData.h,
            w: manualData.w,
            itemNotes: manualData.label || "",
            selectedAddons: {},
            data: manualData.data,
            isEditing: false
        };
    } else {
        const subVal = document.getElementById("subType").value;
        if (!subVal) { alert("Please select a sub-type."); return; }

        const data = findProductData(subVal);
        newItem = {
            id: Date.now(),
            name: subVal,
            qty: parseInt(document.getElementById("quantity").value) || 1,
            h: parseFloat(document.getElementById("height").value) || 1,
            w: parseFloat(document.getElementById("width").value) || 1,
            itemNotes: "",
            selectedAddons: {
                curtain: document.getElementById("addon_curtain")?.checked || false,
                netType: document.getElementById("addon_net_type")?.value || null
            },
            data: JSON.parse(JSON.stringify(data)),
            isEditing: false
        };
    }

    const prices = calculateItemPrice(newItem);
    newItem.unitPrice = prices.unitPrice;
    newItem.totalPrice = prices.totalPrice;
    resultsList.push(newItem);
    renderResults();
}

function processPastedText() {
    const text = document.getElementById("bulkAddText").value;
    const lines = text.split('\n');
    let addedCount = 0;
    let skippedCount = 0;

    lines.forEach(line => {
        line = line.trim();
        if (!line) return;

        const parts = line.split('-').map(p => p.trim());
        if (parts.length < 2) {
            skippedCount++;
            return;
        }

        const label = parts[0];
        const typeCode = parts[1];
        const h = parseFloat(parts[2]) || 1;
        const w = parseFloat(parts[3]) || 1;
        const qty = parseInt(parts[4]) || 1;

        const productInfo = findProductByCode(typeCode);
        if (productInfo) {
            addItem({ name: productInfo.name, h, w, qty, data: productInfo.data, label });
            addedCount++;
        } else {
            skippedCount++;
        }
    });
    alert(`${addedCount} items added successfully. ${skippedCount} lines were skipped due to incorrect format or unknown type code.`);
}


function deleteItem(id) {
    resultsList = resultsList.filter(item => item.id !== id);
    renderResults();
}

function clearAllResults() {
    resultsList = [];
    renderResults();
}

function enterEditMode(id) {
    resultsList.forEach(item => item.isEditing = (item.id === id));
    renderResults();
}

function cancelEdit(id) {
    const item = resultsList.find(i => i.id === id);
    if (item) {
        item.isEditing = false;
        renderResults();
    }
}

function saveItemEdit(id) {
    const item = resultsList.find(i => i.id === id);
    if (item) {
        item.name = document.getElementById(`edit-name-${id}`).value;
        item.qty = parseFloat(document.getElementById(`edit-qty-${id}`).value) || 0;
        item.h = parseFloat(document.getElementById(`edit-h-${id}`).value) || 0;
        item.w = parseFloat(document.getElementById(`edit-w-${id}`).value) || 0;
        item.itemNotes = document.getElementById(`edit-notes-${id}`).value;
        item.unitPrice = parseFloat(document.getElementById(`edit-unitprice-${id}`).value) || 0;
        item.totalPrice = parseFloat(document.getElementById(`edit-totalprice-${id}`).value) || 0;
        item.isEditing = false;
    }
    renderResults();
}

function renderResults() {
    const container = document.getElementById("results");
    container.innerHTML = "";
    let subtotal = 0;

    resultsList.forEach(item => {
        subtotal += item.totalPrice;
        if (item.isEditing) {
            container.innerHTML += `
                <div class="result-item">
                    <div class="edit-form-grid">
                        <div><label>Name</label><input type="text" id="edit-name-${item.id}" value="${item.name}"></div>
                        <div><label>Qty</label><input type="number" id="edit-qty-${item.id}" value="${item.qty}"></div>
                        <div><label>Height</label><input type="number" step="0.01" id="edit-h-${item.id}" value="${item.h}"></div>
                        <div><label>Width</label><input type="number" step="0.01" id="edit-w-${item.id}" value="${item.w}"></div>
                        <div><label>Unit Price</label><input type="number" step="0.01" id="edit-unitprice-${item.id}" value="${item.unitPrice.toFixed(2)}"></div>
                        <div><label>Total Price</label><input type="number" step="0.01" id="edit-totalprice-${item.id}" value="${item.totalPrice.toFixed(2)}"></div>
                    </div>
                    <div style="margin-top: 15px;"><label>Item Notes</label><textarea id="edit-notes-${item.id}">${item.itemNotes}</textarea></div>
                    <div style="text-align: right; margin-top: 10px;">
                        <button onclick="cancelEdit(${item.id})" class="btn-secondary" style="padding: 8px 15px;">Cancel</button>
                        <button onclick="saveItemEdit(${item.id})" class="btn-primary" style="padding: 8px 15px;">Save Changes</button>
                    </div>
                </div>`;
        } else {
            container.innerHTML += `
                <div class="result-item">
                    <div class="item-header">
                        <h4>${item.name}</h4>
                        <div>
                           <button onclick="enterEditMode(${item.id})" class="btn-secondary" style="padding: 6px 12px; margin: 0 5px;">Edit ✏️</button>
                           <button onclick="deleteItem(${item.id})" class="btn-danger" style="padding: 6px 12px; margin: 0;">Delete 🗑️</button>
                        </div>
                    </div>
                    <p><strong>Dimensions:</strong> ${item.h}m x ${item.w}m | <strong>Quantity:</strong> ${item.qty}</p>
                    <p style="font-weight: bold; font-size: 1.1em;">
                        Unit Price: ${item.unitPrice.toFixed(2)} OMR | Total: ${item.totalPrice.toFixed(2)} OMR
                    </p>
                    ${item.itemNotes ? `<p><strong>Notes:</strong> ${item.itemNotes.replace(/\n/g, '<br>')}</p>` : ''}
                </div>`;
        }
    });

    if (resultsList.length > 0) {
        const commission = subtotal * 0.04;
        const total = subtotal + commission;
        container.innerHTML += `
            <div class="summary">
                <div style="display: flex; justify-content: space-between;"><span>Subtotal:</span><span>${subtotal.toFixed(2)} OMR</span></div>
                <div style="display: flex; justify-content: space-between;"><span>Office Commission (4%):</span><span>${commission.toFixed(2)} OMR</span></div>
                <div style="background-color: #00e676; color: #1e1e1e; padding: 15px; border-radius: 5px; text-align: center; margin-top: 10px;">
                    <span style="font-size: 1.3em;">💰 Grand Total</span>
                    <div style="font-size: 2.0em; font-weight: bold;">${total.toFixed(2)} OMR</div>
                </div>
            </div>`;
    }
}

function renderReferenceGuide() {
    const container = document.getElementById('referenceContainer');
    let tableHtml = '<details><summary>Click to see Product Codes Reference</summary><table class="reference-table"><thead><tr><th>Code</th><th>Product Name</th><th>Category</th></tr></thead><tbody>';

    const invertedCodes = {};
    for (const code in productCodes) {
        invertedCodes[productCodes[code]] = code;
    }

    for (const category in productData) {
        for (const product in productData[category]) {
            const code = invertedCodes[product] || 'N/A';
            tableHtml += `<tr><td><strong>${code}</strong></td><td>${product}</td><td>${category}</td></tr>`;
        }
    }

    tableHtml += '</tbody></table></details>';
    container.innerHTML = tableHtml;
}

function formatNumber(num) {
    return Number(num.toFixed(3).replace(/\.?0+$/, ""));
}

function saveAsWord(){
    if (resultsList.length === 0) { alert("There are no results to save."); return; }
    const customerName = document.getElementById('customerName').value || 'Customer';
    const customerPhone = document.getElementById('customerPhone').value || 'N/A';
    const headerHtml = `<div style="width: 100%; font-family: Arial, sans-serif; text-align: center; margin-bottom: 30px; border-bottom: 2px solid #4472C4; padding-bottom: 20px;"><div style="font-size: 26px; font-weight: bold; color: #4472C4; margin-bottom: 15px;">BLUE WAVES SERVICES LLC</div><table width="100%" style="font-family: Arial, sans-serif; font-size: 15px; color: #4472C4; border-collapse: collapse;"><tr><td style="text-align: left; width: 33%;">OMAN – MUSCAT</td><td style="text-align: center; width: 34%;">SR. NO. : 1595256</td><td style="text-align: right; width: 33%;">TEL: 77 22 45 11 – 90 99 88 10</td></tr></table></div>`;
    const customerHtml = `<div style="background-color: #f2f2f2; border: 1px solid #ddd; color: #333; padding: 14px; font-family: Arial, sans-serif; font-size: 17px; margin-bottom: 25px; border-radius: 5px;"><b>Quotation for: </b> ${customerName} - ${customerPhone}</div>`;
    let tableHtml = `<table border="1" width="100%" style="border-collapse: collapse; font-family: Arial, sans-serif; text-align: center; font-size: 14px;">
                        <thead>
                            <tr style="background-color: #4472C4; color: white;">
                                <th style="padding: 10px;">NO</th>
                                <th style="padding: 10px;">H</th>
                                <th style="padding: 10px;">W</th>
                                <th style="padding: 10px;">m²</th>
                                <th style="padding: 10px;">Q</th>
                                <th style="padding: 10px;">RH/LH</th>
                                <th style="padding: 10px;">STYLE</th>
                                <th style="padding: 10px;">PRICE</th>
                                <th style="padding: 10px;">TOTAL</th>
                                <th style="padding: 10px;">DESCRIPTION</th>
                            </tr>
                        </thead>
                        <tbody>`;
    let subtotal = 0;
    let totalShippingCost = 0;
    resultsList.forEach((r, index) => {
        if (r.data && r.data.cbm) {
            const area = r.h * r.w;
            const shippingCost = area * r.data.cbm * SHIPPING_RATE;
            totalShippingCost += shippingCost * r.qty;
        }

        subtotal += r.totalPrice;
        let description = r.name;
        if (r.data && r.data.addons) {
            if(r.selectedAddons.curtain) description += ', with Curtain';
            if(r.selectedAddons.netType) description += `, with ${r.selectedAddons.netType} Net`;
        }
        if(r.itemNotes) description += ` (${r.itemNotes.replace(/\n/g, ', ')})`;

        tableHtml += `<tr>
                        <td style="padding: 10px; font-weight: bold;">${r.itemNotes || `B${index + 1}`}</td>
                        <td style="padding: 10px;">${formatNumber(r.h)}</td>
                        <td style="padding: 10px;">${formatNumber(r.w)}</td>
                        <td style="padding: 10px;">${formatNumber(r.h * r.w)}</td>
                        <td style="padding: 10px;">${r.qty}</td>
                        <td style="padding: 10px;"></td>
                        <td style="padding: 10px;"></td>
                        <td style="padding: 10px; background-color: #f2f2f2;">${formatNumber(r.unitPrice)}</td>
                        <td style="padding: 10px; background-color: #f2f2f2; font-weight: bold;">${formatNumber(r.totalPrice)}</td>
                        <td style="padding: 10px; text-align: left; white-space: pre-wrap;">${description}</td>
                      </tr>`;
    });
    tableHtml += `</tbody></table>`;
    const commission = subtotal * 0.04;
    const grandTotal = subtotal + commission;
    const summaryTable = `<table width="45%" align="right" style="border-collapse: collapse; font-family: Arial, sans-serif; margin-top: 25px; font-size: 15px;"><tbody>
                <tr><td style="padding: 14px; font-weight: bold; border: 1px solid #ccc; font-size: 1.2em;">Subtotal</td><td style="padding: 14px; text-align: right; font-weight: bold; border: 1px solid #ccc; font-size: 1.2em;">${formatNumber(subtotal)} OMR</td></tr>
                <tr><td style="padding: 14px; font-weight: bold; border: 1px solid #ccc; font-size: 1.2em;">Total Shipping Cost</td><td style="padding: 14px; text-align: right; font-weight: bold; border: 1px solid #ccc; font-size: 1.2em;">${formatNumber(totalShippingCost)} OMR</td></tr>
                <tr><td style="padding: 14px; font-weight: bold; border: 1px solid #ccc; font-size: 1.2em;">Office Commission (4%)</td><td style="padding: 14px; text-align: right; font-weight: bold; background-color: #f2f2f2; border: 1px solid #ccc; font-size: 1.2em;">${formatNumber(commission)} OMR</td></tr>
                <tr style="background-color: #4472C4; color: white;"><td style="padding: 16px; font-weight: bold; border: 1px solid #4472C4; font-size: 1.5em;">Grand Total</td><td style="padding: 16px; text-align: right; font-weight: bold; border: 1px solid #4472C4; font-size: 1.9em; vertical-align: middle;">${formatNumber(grandTotal)} OMR</td></tr>
                </tbody></table>`;
    const footerNotesHtml = `<div style="clear: both; font-family: Arial, sans-serif; margin-top: 50px; text-align: center; border-top: 2px solid #4472C4; padding-top: 15px; font-size: 16px; color: #333;"><p style="margin: 5px 0;"><b>*Price includes delivery*</b></p><p style="margin: 5px 0;"><b>*Price does not include installation*</b></p></div>`;
    const finalHtml = `<html xmlns:o='urn:schemas-microsoft-com:office:office' xmlns:w='urn:schemas-microsoft-com:office:word' xmlns='http://www.w3.org/TR/REC-html40'><head><meta charset='utf-8'><title>Quotation for - ${customerName}</title></head><body dir="ltr" style="padding: 20px;">`+ headerHtml + customerHtml + tableHtml +
